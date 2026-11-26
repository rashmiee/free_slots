# Decisions

Short notes on the choices that shaped this project, oldest first. Each one says what was chosen, what else was possible and why.

## 1. Intervals are half-open

2026-11-25

An interval includes its start and excludes its end. The alternative was to include both ends.

A lesson from 9 to 10 and one from 10 to 11 then touch without overlapping, with no special case. It also matches Ruby's `...` range and the default bounds of a PostgreSQL time range.

## 2. No runtime dependencies

2026-11-25

The core works on anything that can be compared and subtracted, such as `Time` or `Integer`. The alternative was to build on Active Support.

A booking library should be usable outside Rails. Time zone handling is the only part that needs help, and it stays in one optional helper.

## 3. A slow version checks the fast one

2026-11-25

Every set operation is tested against a minute-by-minute version that is too slow to ship but hard to get wrong. The alternative was hand-written examples alone.

Interval code fails at the edges, and random input finds edges that examples miss.
