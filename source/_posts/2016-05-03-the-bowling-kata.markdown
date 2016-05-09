---
layout: post
title: "The Bowling Kata"
date: 2016-05-03 20:35:41 -0500
comments: true
categories: 
---
# Getting in to the Mind of a Master

A 'kata' is defined as a "system of individual training exercises for practitioners of karate and other martial arts". Programming isn't exactly martial arts, but as coders we can make use of our own form of kata.

A programming kata is a tool used to teach how to think the way a master thinks, to code as they code. It should be repeated, it should be memorized, and then it should be repeated again.

The Bowling Game Kata is a common one: testing and designing a bowling game from scratch. Let's get started:

### First Test

``` ruby
describe Game do
  it 'initializes a new game' do
    expect(subject).to be_an_instance_of Game
  end
end
```

When run it results in:

``` 
bowling.rb:1:in `<top (required)>': uninitialized constant Game (NameError)
```

So we should probably define a `Game` class huh?

``` ruby
class Game

end
```

That's enough to pass this first test!

```
Finished in 0.00128 seconds (files took 0.15122 seconds to load)
1 example, 0 failures
```

### Second Test

We have a game that initliazes successfully. Now we need to be able to roll.

{% img http://seanbw.com/images/bowling.gif %}

``` ruby
it 'rolls a gutterball' do
  subject.roll 0
end
```

Ruh roh!

```
Finished in 0.00229 seconds (files took 0.18318 seconds to load)
2 examples, 1 failure
```

```
1) Game rolls
     Failure/Error: subject.roll

     NoMethodError:
       undefined method `roll' for #<Game:0x007fbb339d71f0>
     # ./bowling.rb:11:in `block (2 levels) in <top (required)>'
```

Let's write ourselves a roll method for Game. Roll should take the number of pins knocked down in that roll.

```ruby
def roll(number_pins)

end
```

And with that we're now green again!

```
Finished in 0.001 seconds (files took 0.14113 seconds to load)
2 examples, 0 failures
```

This is a good foundation from which to continue the kata!
To be continued...









