# Bug Fix Lab

## Introduction

In this module we're going to look at the fundamental behaviors of programmers.
While it might _feel_ basic, focusing here has a force-multiplying effect.
Improvements here magnify through every second of your time programming.

It's similar to martial arts, dancing, or practicing an instrument. The master
of [Tai Chi][] is known by a perfect, centered [horse stance][]. A master of
[tango][] can be seen by how they take a single step _walking_. Master guitar
players play their _basic_ chords cleanly so that the [tones ring
clearly][paco].

Programmers constantly make the investment in continually improving their
fundamentals. This module will guide you through your (re-)consideration of
your fundamentals. Come back to this lesson as you grow as a programmer to
marvel at how you and your process have improved.

## A Basic Problem

For centuries now, banks have made mortgages available to the public so that
they can buy real estate. While mortgages have evolved a lot, the fundamental
idea is that for a long time, you'll pay interest on the amount you owe the
bank (the original cost of the property). After you have made _all_ your
payments, the bank will have received back their original amount _but will
also_ have all the money you paid in interest. How much is that original
property cost _plus_ the total of all interest payments? How much is the "total
cost" of the loan?

Computers are great at calculating things like this. Let's use a Ruby class to
tell us the answer.

## Formula

We [found a formula][formula] on the internet and decided to code it into Ruby.

![Formula for mortgage total cost](https://curriculum-content.s3.amazonaws.com/pfwtfp/pfwtfp-bug-fix/mortgage_formula.png)

|Letter|Meaning                       |
|------|------------------------------|
|r     |Monthly Interest Rate         |
|P     |Principal Amount on the Loan  |
|N     |Total # of Months for the loan|

_Source: https://www.calcunation.com/calculator/mortgage-total-cost.php_

## Code

Run this code in IRB or inside from a file. The `TotalCostCalculator` will give
you the cost to finance $250,000 at 6.5% for 5 years.

```ruby
class TotalCostCalculator
  attr_reader :description, :cost

  def initialize(description="A sun-drenched paradise", cost=325000, rate=0.02, mortgage_years)
    @description = description
    @cost = cost
    @rate = rate
    @term = 12 * mortgage_years
  end

  def total_loan_cost
    @tlc ||= ((@rate * cost) / 1 - (1 + @rate) ** ( -1 * @term) ) * @term
  end
end

calc = TotalCostCalculator.new("A paradise in Barbados", 250000, 6.5, 5)
puts calc.total_loan_cost
```

## Result

To finance this property, it will cost: $97,500,000.00.

No wonder banks love mortgages so much! To finance my dream-house it will cost
nearly 400 times the cost of the property!

Wait. Does that seem _reasonable_? Using the [calculator site][formula] we see
that the answer _they_ have is closer to $293,492.22. We have a bug.

## Fix It

Most professional programmers spend the majority of their time editing and
maintaining code written by other people. As a result, take this broken code
and make it work. The result of $293,492.22 is right (don't worry about
trailing factions of cents).

Since we're focusing on our fundamentals, keep track of how long this debugging
takes.  Don't let this time stress you out: to improve, we need to know where
we're struggling.

## Next Steps

In the next lesson, we're going to ask you to fill out a survey so that you can
track your improvement.  We'll _also_ provide you our fix.

[formula]: https://www.calcunation.com/calculator/mortgage-total-cost.php
[Tai Chi]: https://en.wikipedia.org/wiki/Tai_chi
[horse stance]: http://taichibasics.com/tai-chi-stances/
[tango]: https://www.youtube.com/watch?v=bXhQNRsH3uc
[paco]: https://www.pri.org/stories/2012-04-23/video-flamenco-music-legend-paco-de-luc
