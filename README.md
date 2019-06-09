<div align="center">
  <h1>
    <br/>
    <br/>
    A/B
    <br/>
    Experiment Hooks
    <br />
    <br />
  </h1>
  <sup>
    <br />
    <br />
    <a href="https://www.npmjs.com/package/use-experiment">
      <img src="https://img.shields.io/npm/v/use-experiment.svg" alt="npm package" />
    </a>
    <a href="https://circleci.com/gh/ju1i4n/use-experiment">
      <img src="https://img.shields.io/circleci/project/ju1i4n/use-experiment/master.svg" alt="CircleCI master" />
    </a>
    <a href="https://codecov.io/gh/ju1i4n/use-experiment">
      <img src="https://codecov.io/gh/ju1i4n/use-experiment/branch/master/graph/badge.svg" />
    </a>
    <br />
  </sup>
  <br />
  <br />
</div>
<br />
<br />

## Install

Using npm:

```sh
npm i use-experiment
```

or using yarn:

```sh
yarn add use-experiment
```


## ```useExperiment()```

```js
const AddToCartButtonExperiment = () => {
  const experimentConfig = {
    id: "3143106098",
    name: "add-to-cart-green",
    variants: [{ name: "control", weight: 50 }, { name: "test", weight: 50 }]
  };
 
  const { variant: { name } } = useExperiment(experimentConfig)

  return (
    if (name === "control") {
       <button class="black">Add to cart</button>
    } else if (name === "test") {
       <button class="green">Add to cart</button>
    }
  )
}
```

## ```useExperimentAsyc()```
```js
const AddToCartButtonExperiment = () => {
  const experimentConfig = {
    fetchVariant: () => {
      // let's assume we call our experiment API that returns variant.
      return new Promise((resolve, reject) => {
        setTimeout(() => {
          // shoud return an object of { name: string, weight: number }.
          resolve({ name: "control", weight: 50 })
        }, 2000)
    })
  }
 
  const { variant: { name }, isLoading } = useExperimentAsync(experimentConfig)
  
  if (isLoading) {
    return <LoadingSpinner />
  }

  return (
    if (name === "control") {
       <button class="black">Add to cart</button>
    } else if (name === "test") {
       <button class="green">Add to cart</button>
    }
  )
}
```


<br />
<br />
<p align="center">
  <a href="./LICENSE"><strong>Unlicense</strong></a> &mdash; public domain.
</p>
