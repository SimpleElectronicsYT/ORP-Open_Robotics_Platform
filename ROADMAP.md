# Roadmap

## Current Phase

### Phase 2: Input stage

#### What is being worked on?

Working on the input stage.

The goal is to make the inputs relatively bullet-proof since the project faces beginners and people not interested in learning electronics - they simply want to make a few connections and have a motor, solenoid, robot etc just work.

The input stage should be robust, offer protections, allow for a wide range of inputs and fail safely.

#### What is working so far?

At this moment, the input stage is working from 2V - 24V. The circuit has reverse protection, isolation, reasonable dissipation in the input resistor, debouncing and current limiting to the MCP23017.

The KiCad diagram for the input stage is being finalized

#### What is blocking progress?

Current testing is showing a skin temperature of the 1kΩ resistor of over 100C at 24V.
This is much too high for a board that will be in the hands of beginners/students, since resistors don't discolor or smoke at this low of a temperature but can cause serious burns and disqualifies plastics as materials for a potential casing.

Found a guide by NASA (https://ntrs.nasa.gov/api/citations/20100020960/downloads/20100020960.pdf) specifying skin temperature maximums for aluminum at 45C - this is my new target.

The plan is to order in 2kΩ resistors and test minimum and maximum input voltages.

I do not want to lose the low input voltage, but safety is a much more important consideration - if low voltage is that important, an add-on module or adding a Darlington transistor might be in order.

## Completed Phases

### Phase 1: Setting up the project

#### What is being worked on?

Documentation and planning, of the system as a whole and parts selection.

Features are being worked into 'core' and 'expansion' categories, it's important to keep feature creep to a minimum.

#### What is working so far?

Nothing at the moment - the project is nearly 100% in the ideation phase, documentation is being created to make it easier to pick up the project from day to day and to give a clear indication of what's in progress and what has been done.

#### What is blocking progress?

I am trying to plan the architecture in a 'big picture' way and at the same time trying to consider all the edge cases of uses and how this will physically be used - but the truth is that a large system like this one that has various separate components is best tweaked while it is being prototyped.

Perfect is the enemy of done, and this is especially problematic in the first prototype, I feel like it will be a lot easier to tweak from there - so the current plan is to charge ahead because nearly nothing will result in a complete loss.