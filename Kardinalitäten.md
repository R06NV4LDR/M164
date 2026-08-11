Zur Darstellung der [Kardinalitäten](https://de.wikipedia.org/wiki/Kardinalit%C3%A4t_(Datenbankmodellierung) "Kardinalität (Datenbankmodellierung)") von binären Beziehungstypen werden die Ziffer _1_, im Sinne von _0 oder 1_, und die Buchstaben _m_ und _n_, im Sinne von _0 bis ∞_ verwendet.

**1:1** (0 oder 1) zu (1 oder 0)

Jede Entität aus der ersten Entitätsmenge kann mit **höchstens einer** Entität aus der zweiten Entitätsmenge in Beziehung stehen, und umgekehrt.

**1:n** | (0 oder 1)zu beliebig vielen

Jede Entität aus der ersten Entitätsmenge kann mit **beliebig vielen** Entitäten aus der zweiten Entitätsmenge in Beziehung stehen. Jede Entität aus der zweiten Entitätsmenge kann mit **höchstens einer** Entität aus der ersten Entitätsmenge in Beziehung stehen.

**m:n** | beliebig viele zu beliebig vielen

Jede Entität aus der ersten Entitätsmenge kann mit **beliebig vielen** Entitäten aus der zweiten Entitätsmenge in Beziehung stehen, und umgekehrt.

### Modifizierte Chen-Notation (MC-Notation)

Die **Modifizierte Chen-Notation** (_Modified Chen Notation_, _MC-Notation_) ist eine Erweiterung der Chen-Notation, bei der die Aussage „kein oder ein Element“ mit dem Buchstaben **c** (_choice_, _can_), und die Aussage „ein oder mehr Element(e)“ mit dem Buchstaben **m** (_must_, _multiple_) angegeben wird. Daher wird _MC_ manchmal auch als _Must-Can_ bezeichnet.

**1:1** (1 zu 1)

Jede Entität der ersten Entitätsmenge steht mit **genau einer** Entität der zweiten Entitätsmenge in Beziehung, und umgekehrt.

**1:c** 1 zu (0 oder 1)

Jede Entität der ersten Entitätsmenge kann mit **höchstens einer** Entität der zweiten Entitätsmenge in Beziehung stehen. Jede Entität der zweiten Entitätsmenge steht mit **genau einer** Entität der ersten Entitätsmenge in Beziehung.

**1:m** 1 zu (mindestens 1)

Jede Entität der ersten Entitätsmenge steht mit **mindestens einer** Entität der zweiten Entitätsmenge in Beziehung. Jede Entität der zweiten Entitätsmenge steht mit **genau einer** Entität der ersten Entitätsmenge in Beziehung.

**1:mc** 1 zu (beliebig vielen)

Jede Entität der ersten Entitätsmenge kann mit **beliebig vielen** Entitäten der zweiten Entitätsmenge in Beziehung stehen. Jede Entität der zweiten Entitätsmenge steht mit **genau einer** Entität der ersten Entitätsmenge in Beziehung.

**c:c** ([1 oder 0] zu [0 oder 1]; entspricht _1:1_ in klassischer Chen-Notation)

Jede Entität der ersten Entitätsmenge kann mit **höchstens einer** Entität der zweiten Entitätsmenge in Beziehung stehen, und umgekehrt.

**c:m** ([0 oder 1] zu [mindestens 1])

Jede Entität der ersten Entitätsmenge steht mit **mindestens einer** Entität der zweiten Entitätsmenge in Beziehung. Jede Entität der zweiten Entitätsmenge kann mit **höchstens einer** Entität der ersten Entitätsmenge in Beziehung stehen.

**c:mc** ([0 oder 1] zu [beliebig vielen]; entspricht _1:n_ in klassischer Chen-Notation)

Jede Entität der ersten Entitätsmenge kann mit **beliebig vielen** Entitäten der zweiten Entitätsmenge in Beziehung stehen. Jede Entität der zweiten Entitätsmenge kann mit **höchstens einer** Entität der ersten Entitätsmenge in Beziehung stehen.

**m:m** ([mindestens 1] zu [mindestens 1])

Jede Entität der ersten Entitätsmenge steht mit **mindestens einer** Entität der zweiten Entitätsmenge in Beziehung, und umgekehrt.

**m:mc** ([mindestens 1] zu [beliebig vielen])

Jede Entität der ersten Entitätsmenge kann mit **beliebig vielen** Entitäten der zweiten Entitätsmenge in Beziehung stehen. Jede Entität der zweiten Entitätsmenge steht mit **mindestens einer** Entität der ersten Entitätsmenge in Beziehung.

**mc:mc** ([beliebig viele] zu [beliebig vielen]; entspricht _m:n_ in klassischer Chen-Notation)

Jede Entität der ersten Entitätsmenge kann mit **beliebig vielen** Entitäten der zweiten Entitätsmenge in Beziehung stehen, und umgekehrt.