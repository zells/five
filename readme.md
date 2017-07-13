# zells (prototype five)

This is the fifth incarnation of a *zells* prototype, implemented with Squeak Smalltalk. Its programming model is described [here](https://github.com/zells/core/blob/master/model.md).

You can find a demo of this prototype [here](https://www.youtube.com/watch?v=T0fLZ8XceLo).

## Installation

Download [Squeak Smalltalk] and run the included image. After you've cloned the project with [git], file-in the files in the [`file-outs` folder](https://github.com/zells/five/blob/master/file-outs) by drag-and-dropping them into the running image.

[Squeak Smalltalk]: http://squeak.org/
[git]: https://git-scm.com/

## Usage

Paste the following text into a Workspace and execute ('do-it') each line individually.

### Create a Dish

Create a new, empty Dish and put it somewhere.

	(Z5DishMorph for: Z5Dish new) openInWindow openInHand.

### Simple back-and-forth

Zells can react to received Signals. Drop these Zells into the Dish and click on them.

	"This Zell emits a Signal when clicked"
	(Z5ButtonZellMorph emitting: #hey) openInHand.

	"Click on this Zell to see all Signals it receives."
	(Z5ListenerZellMorph new) openInHand.

	"Simple Zell that responds with 'ho' to every 'hey' it hears"
	(Z5ZellMorph for: (Z5DynamicZell doing: [ :s :z | (s isA: '"hey"') ifTrue: [z accept: s. z emit: (Z5StemZell thatIsA: '"ho"')]])) openInHand.

### Emitter

This Zell can be used to emit any Signal. Click on it to open the drop zone and drop the next Zell into it.

	(Z5EmitterZellMorph new) openInHand.

	(Z5StemZellMorph for: (Z5StemZell thatIsA: '"Hello World"')) openInHand.

### Turtle

The *Turtle* can go forward, turn and jump back to its starting position using these three Signals.
	
	(Z5TurtleZellMorph new) openInHand.

	(Z5ButtonZellMorph emitting: #go) openInHand.
	(Z5ButtonZellMorph emitting: #turn) openInHand.
	(Z5ButtonZellMorph emitting: #reset) openInHand.
	
	"This Signal will make the Turtle go forward a little more"
	(Z5StemZellMorph for: (Z5StemZell named: #go thatIsA: '30')) openInHand.

### Clock

A *Clock* emits its Signals with every tick. Click on the Clock to open its editor. Then drop a "go" and a "turn" Signal into it. Then emit the "start" Signal (by dropping it into the Emitter window) to start it. The other two Signals stop and clear the Clock.

	Z5ClockZellMorph new openInHand.

	(Z5ButtonZellMorph emitting: #start) openInHand.
	(Z5ButtonZellMorph emitting: #stop) openInHand.
	(Z5ButtonZellMorph emitting: #clear) openInHand.

### Arithmetic

You can do simple arithmetic by dropping a Number named *distance* into the Dish and emit the following Signal to add `4` to it. Since distance *is* `4`, it will emit a Signal with the *result* `7`. You can also ask distance to *be* `1`.

	(Z5StemZellMorph for:(Z5NumberZell named:#distance thatIsA: '3')) openInHand.

	(Z5StemZellMorph for: (Z5StemZell new haveA: (Z5StemZell named: #target thatIsA: '"distance"'); haveA: (Z5StemZell named: #add thatIsA: '4'); haveA: (Z5StemZell named: #tellResultTo thatIsA: '"bob"'))) openInHand

	(Z5StemZellMorph for: (Z5StemZell new haveA: (Z5StemZell named: #target thatIsA: '"distance"'); haveA: (Z5StemZell named: #be thatIsA: '1'))) openInHand.

### Spiral

To make the Turtle draw a spiral, stop and clear the Clock and add these three Signals and start it.

	(Z5StemZellMorph for: (Z5StemZell named: #go thatIsA: 'distance')) openInHand.

	(Z5StemZellMorph for: (Z5StemZell new haveA: (Z5StemZell named: #target thatIsA: '"distance"'); haveA: (Z5StemZell named: #increaseBy thatIsA: '0.1'))) openInHand.

	(Z5StemZellMorph for: (Z5StemZell thatIsA: '"turn"')) openInHand.

