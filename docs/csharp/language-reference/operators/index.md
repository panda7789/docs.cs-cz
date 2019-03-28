---
title: 'C#operátory'
ms.date: 04/04/2018
f1_keywords:
  - cs.operators
helpviewer_keywords:
  - 'boolean operators [C#]'
  - 'expressions [C#], operators'
  - 'logical operators [C#]'
  - 'operators [C#]'
  - 'Visual C#, operators'
  - 'indirection operators [C#]'
  - 'assignment operators [C#]'
  - 'shift operators [C#]'
  - 'relational operators [C#]'
  - 'bitwise operators [C#]'
  - 'address operators [C#]'
  - 'keywords [C#], operators'
  - 'arithmetic operators [C#]'
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
---
# <a name="c-operators"></a>C#operátory

Jazyk C# poskytuje mnoho operátorů, které jsou symboly, které určují operace, které (matematické, indexování, volání funkce atd.) provést ve výrazu. Je možné [přetížení](../../programming-guide/statements-expressions-operators/overloadable-operators.md) mnoho operátorů, chcete-li změnit jejich význam při aplikování na uživatelem definovaného typu.

Operace interních typů (například `==`, `!=`, `<`, `>`, `&`, `|`) jsou obecně povoleny na výčet (`enum`) typy.

Níže uvedených částech najdete seznam operátorů jazyka C# od nejvyšší prioritu, takže nejnižší. Operátory v jednotlivých částech sdílet stejnou úrovní priority.

## <a name="primary-operators"></a>Primární operátory

Jedná se o nejvyšší priorita operátorů.

[x.y](member-access-operator.md) – přístup ke členu.

[x?. y](null-conditional-operators.md) – přístup Podmíněný člen s hodnotou null. Vrátí `null` pokud levý operand je vyhodnocen jako `null`.

[x? [y] ](null-conditional-operators.md) -index podmíněného přístupu s hodnotou null. Vrátí `null` pokud levý operand je vyhodnocen jako `null`.

[f(x)](invocation-operator.md) – funkce volání.

[&#91;x&#93; ](index-operator.md) – indexování agregovaný objekt.

[x ++](arithmetic-operators.md#increment-operator-) – Příponové operátory Inkrementace. Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).

[x--](arithmetic-operators.md#decrement-operator---) – snížení příponového operátora. Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).

[nové](../keywords/new-operator.md) – typ vytváření instancí.

[typeof](../keywords/typeof.md) – vrátí <xref:System.Type> objekt představující operand.

[checked](../keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.

[unchecked](../keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení. Toto je výchozí chování kompilátoru.

[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.

[Delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.

[operátor sizeof:](../keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.

[->](dereference-operator.md) – přístup přes ukazatel v kombinaci s přístup ke členu.

## <a name="unary-operators"></a>Unární operátory

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[+ x](addition-operator.md) – vrátí hodnotu x.

[-x](subtraction-operator.md) – číselné negace.

[\!x](logical-negation-operator.md) – Logická negace.

[~ x](bitwise-complement-operator.md) – bitového doplňku.

[++ x](arithmetic-operators.md#increment-operator-) – předponového. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).

[--x](arithmetic-operators.md#decrement-operator---) – předponového. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).

[(T) x](invocation-operator.md) – typ přetypování.

[operátor await](../keywords/await.md) – čeká `Task`.

[& x](and-operator.md) – adresu.

[* x](multiplication-operator.md) – přesměrování.

## <a name="multiplicative-operators"></a>Operátory násobení

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x * y](arithmetic-operators.md#multiplication-operator-) – násobení.

[x a y](arithmetic-operators.md#division-operator-) – dělení. Pokud jsou operandy celých čísel, výsledek je celé číslo zkráceno směrem k nule (například `-7 / 2 is -3`).

[x, % y](arithmetic-operators.md#remainder-operator-) – zbytek. Pokud jsou operandy celých čísel, vrátí zbytek dělicí x y.  Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.

## <a name="additive-operators"></a>Operátory sčítání

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x + y](arithmetic-operators.md#addition-operator-) – přidání.

[x-y](arithmetic-operators.md#subtraction-operator--) – odčítání.

## <a name="shift-operators"></a>Operátory posunutí

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x <\< y](left-shift-operator.md) – posunutí bitů doleva a vyplnit nula na pravé straně.

[x >> y](right-shift-operator.md) – posunutí bitů doprava. Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka. Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.

## <a name="relational-and-type-testing-operators"></a>Operátory relační a typové zkoušky

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x \< y](less-than-operator.md) – menší než (true, pokud x je menší než y).

[x > y](greater-than-operator.md) – větší než (true, pokud x je větší než y).

[x \<= y](less-than-equal-operator.md) – menší než nebo rovno.

[x > = y](greater-than-equal-operator.md) – větší než nebo rovna hodnotě.

[je](../keywords/is.md) – typ kompatibility. Vrátí true, pokud vyhodnocený levý operand může být převeden na typ určený v pravý operand (statického typu).

[jako](../keywords/as.md) – převod typu. Vrátí levý operand přetypování na typ určený pravý operand (statického typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.

## <a name="equality-operators"></a>Operátory rovnosti

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x == y](equality-operators.md#equality-operator-) – rovnosti. Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test). Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.

[x! = y](equality-operators.md#inequality-operator-) – není rovno. Viz komentář `==`. Pokud typ přetížení `==`, pak musí přetížení `!=`.

## <a name="logical-and-operator"></a>Logický operátor AND

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x & y](and-operator.md) – logický operátor or bitový AND. Obecně můžete s celočíselnými typy a `enum` typy.

## <a name="logical-xor-operator"></a>Logický operátor XOR

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x ^ y](xor-operator.md) – logické a bitové operace XOR. Obecně můžete s celočíselnými typy a `enum` typy.

## <a name="logical-or-operator"></a>Logický operátor OR

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x &#124; y](or-operator.md) – logické a bitové operace OR. Obecně můžete s celočíselnými typy a `enum` typy.

## <a name="conditional-and-operator"></a>Podmiňovací operátor AND

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x & & y](conditional-and-operator.md) – logickým operátorem a. Pokud je první operand vyhodnocen na hodnotu false, pak C# není vyhodnocen Druhý operand.

## <a name="conditional-or-operator"></a>Podmiňovací operátor OR

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x &#124; &#124; y](conditional-or-operator.md) – logický operátor OR. Pokud je první operand vyhodnocen na hodnotu true, pak C# není vyhodnocen Druhý operand.

## <a name="null-coalescing-operator"></a>Operátoru nulového sjednocení

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x?? y](null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.

## <a name="conditional-operator"></a>Podmíněný operátor

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[t? x: y](conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.

## <a name="assignment-and-lambda-operators"></a>Operátory přiřazení a Lambda

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x = y](assignment-operator.md) – přiřazení.

[x += y](addition-assignment-operator.md) – přírůstku. Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu. Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# přidá jako obslužné rutiny události.

[x-= y](subtraction-assignment-operator.md) – sníží. Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu. Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# odebere jako obslužné rutiny události

[x * = y](multiplication-assignment-operator.md) – přiřazení násobení. Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x / = y](arithmetic-operators.md#compound-assignment) – přiřazení dělení. Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.

[x % = y](arithmetic-operators.md#compound-assignment) – remainder přiřazení. Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.

[x & = y](and-assignment-operator.md) – a přiřazení. A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x &#124;= y](or-assignment-operator.md) – přiřazení OR. NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x ^ = y](xor-assignment-operator.md) – XOR přiřazení. XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x << = y](left-shift-assignment-operator.md) – přiřazení posunutí doleva. Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.

[x >> = y](right-shift-assignment-operator.md) – přiřazení posunutí doprava. Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.

[=>](lambda-operator.md) – deklaraci lambda.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#](../../index.md)
- [Přetížitelné operátory](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [Klíčová slova jazyka C#](../keywords/index.md)