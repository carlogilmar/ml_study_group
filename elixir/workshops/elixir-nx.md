# Elixir NX Basic Workshop

```elixir
Mix.install([
  {:nx, "~> 0.7.2"}
])
```

## 🚀 Elixir NX Basics Workshop

| Table of contents         |
| ------------------------- |
| 1. Installation           |
| 2. Tensors Basics         |
| 3. Tensor Aware Functions |
| 4. Numerical Definitions  |

### 1. Installation

Include the depedency in your mix file. Remember NX is another way to program in Elixir.

<!-- livebook:{"force_markdown":true} -->

```elixir
 {:nx, "~> 0.5"}
```

### 2. Tensors: The center of the NX API

Data structures to represent **multi-dimensional** data using typed data. It could be defined as a **multi-dimensional array with a shape and type**.

The tensors rely in **tensor-aware operators** optimized for this kind of operations, instead of use Enum as normally we use in Elixir.

Tensor is astruct but remember is an **opaque data type**.

* Tensor creation
* Access to tensor values
* Access to one dimension
* Access to a range
* Get the shape
* Reshape

```elixir
## 2.1 Tensor Creation from lists

tensor =
  Nx.tensor(
    [
      # <-- Array, row 0 
      [1, 2, 3],
      # <-- Array, row 1
      [4, 5, 6]
    ],
    # <-- Options
    names: [:y, :x]
  )
```

```elixir
## 2.2 Access to tensor values

# <- access row 0, element 0 from our tensor 
tensor[0][0]

## Returns:

## #Nx.Tensor<. <-- Data Structure
##   s64 <-- Tensor type
##   1 <-- Value from row 0, element 0
##  >
```

```elixir
## 2.3 Access to one dimension

# <-- Request y the values on x=1 
tensor[x: 1]
```

```elixir
## 2.4 Acces to a range

# <-- This will give you the array with values in 0 position.
tensor[y: 0]
```

```elixir
## 2.5 Get the shape of the tensor
# <-- Output: {2, 3}
Nx.shape(tensor)
```

```elixir
## 2.6 Creating new tenson from an existing tensor

## <-- Declare a new tensor, one row, 4 elements
t =
  Nx.tensor([1, 2, 3, 4], names: [:x])

## <-- This will take the tensor and create a new one
new_t =
  Nx.reshape(t, {2, 2}, names: [:new_x, :new_y])
```

### 3. Tensor Aware Functions

Nx have functions to operate over tensors.

* Get cosine
* Aggregates tensor content
* Substract
* Broadcast

```elixir
## 3.1 Get cosine from a tensor

# <-- A tensor can be a scalar
pi = Nx.tensor(3.1415, type: :f32)

Nx.cos(pi)

my_tensor = Nx.tensor([[1, 2], [3, 4]], names: [:y, :x])

Nx.cos(my_tensor)

## 3.2 Aggreates the tensor content

Nx.sum(my_tensor)

Nx.sum(my_tensor, axes: [:x])
```

```elixir
## 3.3 Matrix substrack 

my_tensor2 = Nx.tensor([[5, 6], [7, 8]])

Nx.subtract(my_tensor2, my_tensor)
```

```elixir
## 3.4 Broadcasts 

Nx.broadcast(100, {2, 2, 2})
```

```elixir
## <-- It can take another tensor to convert it into a similar data structure
Nx.broadcast(1, my_tensor2)
```

```elixir
# <-- This will apply broadcast internally 
Nx.subtract(my_tensor, 1)

Nx.broadcast(Nx.tensor([1, 2]), {2, 2})
```

### 4. Numerical Definitions defn

`defn` macro simplifies the expression of functions for tensors. This set of definitions have advantages over normal elixir functions: tensor-aware (optimized for tensors) and building computation graph (JIT compilation).

* Tensor-aware
* JIT Compilation
* Run on accelerate numerical processors

How to start to use this?

<!-- livebook:{"force_markdown":true} -->

```elixir
import Nx.Defn
```

```elixir
# 4.1 Creating a new module with numerical definitions

defmodule TensorMath do
  import Nx.Defn

  defn subtract(a, b) do
    a - b
  end
end

t1 = Nx.tensor([1, 2])
t2 = Nx.tensor([3, 4])

## <-- You can use tensors in params
TensorMath.subtract(t1, t2)
```
