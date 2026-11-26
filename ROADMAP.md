# Roadmap

Six slices. Each one is small and ends with passing tests. A slice is finished when its check passes, not when the code exists.

- [ ] **1. Skeleton and Interval.** The gem layout, tests and lint in CI on the supported Ruby versions, and an `Interval` with a start and an end that knows whether it overlaps or touches another. Done when the specs cover overlap, touching ends and an empty interval, and CI is green.
- [ ] **2. Interval sets.** A sorted set of intervals that never overlap, with merge, intersection and difference. Done when each operation matches a slow minute-by-minute version on random input.
- [ ] **3. One resource.** Availability minus busy time, with buffer before and after. Free time is cut into slots of a given length on a given step, inside a window and after a minimum notice. Done when the specs cover a buffer that swallows a gap, a slot that ends exactly at closing time and a window with nothing free.
- [ ] **4. Several resources.** A slot needs all of the listed resources, or any one from a pool. Each slot says which resources it uses. Done when the results match the slow version for generated schedules with three resources and a pool.
- [ ] **5. Explain and opening hours.** `explain` says why a time is not free. A helper turns weekly opening hours in a time zone into concrete intervals. Done when the specs cover a daylight saving change in both directions and a benchmark with ten thousand bookings is in the repo.
- [ ] **6. Release.** A README with examples, a changelog and version 0.1.0 on RubyGems. Done when a fresh project can install the gem and run the README example, and Lessonlane uses it for its slot search.
