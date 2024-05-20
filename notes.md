# Week 1

| Sketch notes

# Week 2

### Multiple features

![image](https://github.com/carlogilmar/ml_study_group/assets/17634377/8e618a84-10c0-4890-a4ef-a32cc6a5cf51)

- Linear regression `Fw,b(x) = wx + b` for one variable.
- Multiple variables, multiple features, multiple data sets.
- We use row vectors. `X = [1416 3 2 40]`
- For multiple features our model change to `Fw,b(x) = w1x1 + w2x2 + w3x3 + w4x4 + b` where `X: different features`

`Multiple features`

![image](https://github.com/carlogilmar/ml_study_group/assets/17634377/0459e9f9-040b-4ac6-96ee-ff24f4b2544c)

**Linear Regression with Multiple Variables**

- Numpy implements vectorization `np.dot(w,x)`

---

```
Gradient Descent
- 16 parameters
- You'll have to calculate 16 derivatives
- You can calculate this using Vectorization by implementing `np.array`
```

<img width="925" alt="image" src="https://github.com/carlogilmar/ml_study_group/assets/17634377/3d08400b-f342-4683-80b3-a64010561655">
