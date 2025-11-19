# Applied Practice: Class Diagram Self Check

## Instructions

**Diagram Description:**
The diagram shows a university system with `Professor`, `Student`, `Seminar`, `Course`, and `Address`.

**Task:** Determine if the following statements are True or False based on the diagram rules (multiplicities).

1. **"There are visiting professors and non-visiting professors."**
    * *Hint:* Look at the `lives at` relationship. Is it `0..1` or `1`?
2. **"There can be professors instructing no seminar."**
    * *Hint:* Look at the association between `Professor` and `Seminar`.
3. **"There can be seminars without students."**
    * *Hint:* Look at the `enrolled in` multiplicity.
4. **"It is not possible that a professor and a student have the same address."**
    * *Hint:* Can two objects point to the same `Address` object?
5. **"There can be no more than 25 participants in a seminar."**
    * *Hint:* Is there a constraint `{max=25}` visible?

---

## Solution (from Slide 48)

1. **True.** (If `lives at` is 0..1).
2. **True.** (If `instructs` is 0..*).
3. **True.**
4. **False.** (They can share the same address object).
5. **False.** (Diagram shows `*`, implies no upper limit unless constrained).
