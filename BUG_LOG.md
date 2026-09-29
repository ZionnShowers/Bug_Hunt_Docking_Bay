# Docking Bay Bug Log

**Name:** __Zionn Showers_______________________

Log **every** bug as you fix it, one row per bug. There are **15**: 5 syntax, 4 runtime, 6 logic.

- **File**: which file the bug was in, e.g. `Services/ShipService.cs`
- **Line**: the line number where you made the fix
- **Kind**: `Syntax`, `Runtime` or `Logic`
- **What was wrong**: what the code did, and how you noticed (the build error, the exception, or the wrong result in Postman)
- **How I fixed it**: exactly what you changed

## Example (not one of the 15)

| # | File | Line | Kind | What was wrong | How I fixed it |
|---|------|------|------|----------------|----------------|
| 0 | `Services/ExampleService.cs` | 22 | Logic | `GET /api/example/cheapest` returned the **most** expensive item. The list was sorted with `OrderByDescending(i => i.Price)`, so the first item was the priciest. | Changed `OrderByDescending` to `OrderBy`. |

## My bugs

| # | File | Line | Kind | What was wrong | How I fixed it |
|---|------|------|------|----------------|----------------|
| 1 |ShipService.cs |10 |Syntax |Missing , |Added , |
| 2 |Ship.cs |6 |Syntax |Missing ; | Added ; |
| 3 |ShipsController.cs |32 |Syntax |Missing end bracket |Added end bracket |
| 4 |PilotsController.cs |13 |Syntax |PilotsController name gives error |Fixed Names |
| 5 |IPilotService.cs |9 |Syntax |List is spelled with lowercase L |Changed L in List into uppercase |
| 6 |ShipsController.cs |37 |Logical |Looking for ship id doesn't work |Changed != into == |
| 7 |Program.cs |8 |Runtime?? |Ship Services are pasted twice |Replaced with Pilot Services |
| 8 |ShipServices |21 |Runtime |Gives error when looking for a number out of range |Changed First to FirstOrDefault |
| 9 |ShipsController.cs |49 |Logical |Doesn't give correct id output |changed Ok into CreatedAtAction |
| 10 |ShipService.cs |54 |Logical |Adds 100 to the given fuel percent |Changed += into = |
| 11 |ShipService.cs | 62-68|Runtime |Gives error when attempting to delete |Changed foreach into for statements |
| 12 |PilotService.cs |50 |Logical |Sets Flight hours to Log hours instead of adding |Changed = to += |
| 13 |PilotsController.cs |62 |Logical |Does not give error if log hours is set to 0 |Changed < to <= |
| 14 |PilotService.cs |49-52 |Runtime |Gives error when finding id that doesn't exist |Added check to see if id exists |
| 15 |PilotService.cs |38-39 |Logical |Doesn't add more id's |Added new line with _nextId++; |

## Tally

| Kind | Found |
|------|-------|
| Syntax | __5_ / 5 |
| Runtime | _4__ / 4 |
| Logic | _6__ / 6 |

## Reflection

Answer each in 2–3 sentences.

1. Which bug took you the longest to find? What finally led you to it?
2. Pick one **runtime** error. What exception did it throw, and how did the error message help
   you find the line?
3. `DELETE /api/ships/3` crashed with `Collection was modified`. Why can't a `foreach` loop keep
   going after you remove something from the list it's looping over?
4. Every `/api/pilots` request crashed until you fixed one line in `Program.cs`. Explain what
   dependency injection was trying to do and why it failed.
5. Several logic bugs were a single character, like `!=` versus `==`, `<` versus `<=`, or
   `=` versus `+=`. Why doesn't the compiler catch these?
6. Some bugs hid until you fixed a different one. Give one example.

ANSWER:
1. Bug 11 took me the longest. I had to write new lines of code to make sense within the context of the program while trying not to go too far.
2. I don't remember exception it gave me, but I believe it was something with bug 8. I think it told me the the number was not an acceptable because there was no function in case number wasn't in range.
3.  I don't remember excactl. However, I think it may be because it tries to delete everything, including the ones it doesn't have values for.
4. It was only loading the ships controlls. There was nothing for the pilots, so I had to include ones to make it work.
5. Because they are viable inputs and can fit within any context. The program only checks for spelling and coding errors.
6. Most of these bugs appeared after renaming some lines of code that didn't match up with previously written lines of code. For example, renaming some of the .cs files caused me to fix a bunch of the names inside other .cs files.