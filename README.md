# free_slots

A small Ruby library that answers one question. Given when things are available and when they are already busy, which time slots are free?

It is meant for booking systems where one appointment needs several things at once, such as a person, a room and a vehicle, and where rules like buffer time and minimum notice apply.

Status - just started and not released yet. The plan is in [ROADMAP.md](ROADMAP.md) and the choices behind it are in [DECISIONS.md](DECISIONS.md).

## Planned usage

This is a sketch of where the API is heading. It will change while the library is being built.

```ruby
instructor = FreeSlots::Resource.new(
  available: [monday_9_to_17],
  busy: [lesson_10_to_11],
  buffer_after: 15 * 60
)
car = FreeSlots::Resource.new(available: [monday_8_to_18], busy: [])

FreeSlots.find(
  resources: [instructor, car],
  duration: 60 * 60,
  step: 15 * 60,
  within: monday_8_to_18
)
# => slots starting at 09:00, 11:15, 11:30 and so on
```

## Goals

- Plain Ruby with no runtime dependencies.
- Several resources at once. Either all of them must be free, or any one from a pool, such as any of three cars.
- Buffer time before and after a booking, minimum notice, and slots aligned to a step.
- An `explain` call that says why a given time is not free and which resource is in the way.
- Tested against a slow, obviously correct version on random input.
- A benchmark and a note on complexity.

## License

MIT
