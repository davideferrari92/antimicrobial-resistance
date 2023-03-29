# Symbolic Regression predictive models for Bloodstream Infection and Antimicrobial Resistance

In this repository you can find the predictive models generated using the code in the [Multiobjective Symbolic Regression repository](https://github.com/davideferrari92/multiobjective_symbolic_regression) for the prediction of Bloodstream Infection and Antimicrobial Resistance in patients admitted to ICU.

## Loading the models

You can use this code to load the models:

```python
from symbolic_regression.SymbolicRegressor import SymbolicRegressor

PATH = './models/_blood_plus_bce_auc_f1.save'
sr = SymbolicRegressor(client_name='amr').load_model(PATH)
```

## Exploring the models and their performance

You can find all models in the list

```python
sr.population: List[Program]
```

e.g. this prints the first model:

```python
sr.population[0].program: Program
```

And the performance measures on the training set are stored in

```python
sr.population[0].fitness: Dict[str, float]
```

## Executing the models

You can use the models to predict the outcome of a new patient using the `evaluate` method:

NB: make sure that the variable names are the same as what you find in the programs because they rely on their name, not their order.

```python
sr.population[0].evaluate(data: Union[dict, pd.Series, pd.DataFrame]): float
```