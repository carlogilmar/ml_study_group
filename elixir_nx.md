## Machine Learning in Elixir

### Get comfortable with Nx

- Thinking in tensors
- Bad data leads to bad models
- Tensor is a multidimensional array. 
- Tensor definition comes from the ubiquity in numerical computing.
- NX.Tensor is designed for two goals in mind: flexiblity and performance.
- Multidimensional array is the most common data structure in machine learning.
- Nx Tensors are different than other data structure in elixir.
- EXLA is used to accelerate Nx programming.

`tensors`
- A tensor is `Nx.tensor([1, 2, 3])`
- Tensors have a numeric type: signed integer, unsigned integer, float, brain float, complex. `
Nx.tensor(1.0e-45, type: {:f, 64})`
- Tensors have homogenous type.
- Tensors have a shape.
- Named tensors: `Nx.tensor([[1, 2, 3], [4, 5, 6]], names: [:x, :y])`
- Tensors have data `Nx.to_binary(a)`
- Tensors are immutable, every operation returns a new tensor

`Nx Operations`
- Cast to type: `Nx.as_type(tensor, {:f, 32})`
- Modify shape: `Nx.reshape({1, 3, 1})`
- `Nx.abs(tensor)`
- `Nx.add(tensor1, tensor2)` or `Nx.add(5, Nx.tensor([1, 2, 3]))` (Broadcasting)
- `Nx.multiply(t1, t2)`
- Reductions: `Nx.sum(tensor)` 

`Defn definitions`
- In your module import `import Nx.Defn`
- The function `defn` can be JIT compilet on the CPU or GPU
- You can use backends to interpret your code
- `Nx.default_backend(EXLA.Backend)` EXLA backend to speed.


