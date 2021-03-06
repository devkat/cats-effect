---
layout: docs
title:  "Data Types"
position: 1
---

# Data Types

{:.responsive-pic}
![datatypes cheat sheet](../img/datatypes-cheat-sheet.png)

### [IO](./io.html)
A data type for encoding synchronous and asynchronous side effects as pure values

### [SyncIO](./syncio.html)
A data type for encoding synchronous side effects as pure values

### [Fiber](./fiber.html)
A pure result of a [Concurrent](../typeclasses/concurrent.html) data type being started concurrently and that can be either joined or canceled

```scala
def cancel: F[Unit]
def join: F[A]
```

### [Resource](./resource.html)
A resource management data type that complements the `Bracket` typeclass

### [Clock](./clock.html)
Provides the current time, used for time measurements and getting the current clock

```scala
def realTime(unit: TimeUnit): F[Long]
def monotonic(unit: TimeUnit): F[Long]
```

### [ContextShift](./contextshift.html)
 A pure equivalent of an `ExecutionContext`. Provides support for cooperative yielding and shifting execution, e.g. to execute blocking code on a dedicated execution context.

 Instance for `IO` is required by `Concurrent[IO]`

```scala
def shift: F[Unit]
def evalOn[A](ec: ExecutionContext)(f: F[A]): F[A]
```

### [Timer](./timer.html)
 A pure scheduler. Provides the ability to get the current time and delay the execution of a task with a specified time duration.

 Instance for `IO` is required by `IO.sleep`, `timeout`, etc.

```scala
def clock: Clock[F]
def sleep(duration: FiniteDuration): F[Unit]
```
