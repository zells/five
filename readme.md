# zells (prototype five)

This is the fifth incarnation of a *zells* prototype, implemented with Squeak Smalltalk. Its programming model is described [here](https://github.com/zells/core/blob/master/model.md).

You can find a demo of this prototype [here](https://www.youtube.com/watch?v=T0fLZ8XceLo).

## Installation

Download [Squeak Smalltalk] and run the included image. After you've cloned the project with [git], file-in the files in the [`file-outs` folder](https://github.com/zells/five/blob/master/file-outs) by drag-and-dropping them into the running image.

[Squeak Smalltalk]: http://squeak.org/
[git]: https://git-scm.com/

## Usage

Paste the code blocks into a *workspace* and execute (*do-it*) each line individually.

### Reception

```smalltalk
(Z5ListenerZellMorph new) openInHand.

(Z5StemZellMorph for: (Z5StemZell thatIsA: '"Hello World"')) openInHand.
```

### Control

```smalltalk
(Z5TurtleZellMorph new) openInHand.

(Z5StemZellMorph for: (Z5StemZell named: #go)) openInHand.
(Z5StemZellMorph for: (Z5StemZell named: #turn)) openInHand.
(Z5StemZellMorph for: (Z5StemZell named: #reset)) openInHand.
```

### Transmission

```smalltalk
(Z5DishMorph for: Z5Dish new) openInWindow openInHand.

(Z5EmitterZellMorph new) openInHand.
```

```smalltalk
(Z5ButtonZellMorph new) openInHand.

(Z5StemZellMorph for: (Z5StemZell named: 'go' thatIsA: '5')) openInHand.
(Z5StemZellMorph for: (Z5StemZell named: 'turn' thatIsA: '30')) openInHand.
```

### Reaction

```smalltalk
(Z5StemZellMorph for: (Z5StemZell named: #hey)) openInHand.

(Z5ZellMorph for: (Z5DynamicZell doing: [ :s :z | (s name = #hey) ifTrue: [z emit: (Z5StemZell named: #ho)]])) openInHand.
```

### Repetition

```smalltalk
Z5ClockZellMorph new openInHand.

(Z5StemZellMorph for: (Z5StemZell named: #start)) openInHand.
(Z5StemZellMorph for: (Z5StemZell named: #stop)) openInHand.
(Z5StemZellMorph for: (Z5StemZell named: #clear)) openInHand.
```

### Arithmetic

```smalltalk
(Z5StemZellMorph for:(Z5NumberZell named:#distance thatIsA: '3')) openInHand.

(Z5StemZellMorph for: (Z5StemZell new haveA: (Z5StemZell named: #target thatIsA: '"distance"'); haveA: (Z5StemZell named: #add thatIsA: '4'); haveA: (Z5StemZell named: #tellResultTo thatIsA: '"bob"'))) openInHand

(Z5StemZellMorph for: (Z5StemZell new haveA: (Z5StemZell named: #target thatIsA: '"distance"'); haveA: (Z5StemZell named: #be thatIsA: '1'))) openInHand.
```

### Spiral

```smalltalk
(Z5StemZellMorph for: (Z5StemZell named: #go thatIsA: 'distance')) openInHand.

(Z5StemZellMorph for: (Z5StemZell new haveA: (Z5StemZell named: #target thatIsA: '"distance"'); haveA: (Z5StemZell named: #increaseBy thatIsA: '0.1'))) openInHand.

(Z5StemZellMorph for: (Z5StemZell named: #turn)) openInHand.
```
