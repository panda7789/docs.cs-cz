---
title: C#Operators – C# odkaz
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 0cd0a06dc919ecf11f1a3d343fe8ff023a5f8524
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609916"
---
# <a name="c-operators-c-reference"></a>C#operátory (C# odkaz)

C#poskytuje řadu předdefinovaných operátory podporovaných předdefinovaných typů. Například [aritmetické operátory](arithmetic-operators.md) provádění aritmetických operací s operandy předdefinovaných číselných typů a [logické logické operátory](boolean-logical-operators.md) provádí logické operace s [bool ](../keywords/bool.md) operandy.

Uživatelem definovaný typ může přetížit některé operátory definovat odpovídající chování pro operandy typu. Další informace najdete v tématu [přetížení operátoru](operator-overloading.md).

Následující části seznamu C# operátory od nejvyšší prioritu, takže nejnižší. Operátory v jednotlivých částech sdílet stejnou úrovní priority.

## <a name="primary-operators"></a>Primární operátory

Jedná se o nejvyšší priorita operátorů.

[x.y](member-access-operators.md#member-access-operator-) – přístup ke členu.

[x?. y](member-access-operators.md#null-conditional-operators--and-) – přístup Podmíněný člen s hodnotou null. Vrátí `null` pokud levý operand je vyhodnocen jako `null`.

[x? [y] ](member-access-operators.md#null-conditional-operators--and-) – prvek Podmíněné pole s hodnotou null, nebo zadejte přístup indexeru. Vrátí `null` pokud levý operand je vyhodnocen jako `null`.

[f(x)](member-access-operators.md#invocation-operator-) – metoda volání nebo vyvolání delegáta.

[&#91;x&#93; ](member-access-operators.md#indexer-operator-) – element pole nebo typ přístup indexeru.

[x ++](arithmetic-operators.md#increment-operator-) – Příponové operátory Inkrementace. Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).

[x--](arithmetic-operators.md#decrement-operator---) – snížení příponového operátora. Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).

[nové](new-operator.md) – typ vytváření instancí.

[typeof](type-testing-and-conversion-operators.md#typeof-operator) – vrátí <xref:System.Type> objekt představující operand.

[checked](../keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.

[unchecked](../keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení. Toto je výchozí chování kompilátoru.

[Default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.

[nameof](../keywords/nameof.md) -získá jednoduchého (nekvalifikovaného) název proměnné, typ nebo člena jako konstanty typu řetězec.

[Delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.

[operátor sizeof:](../keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.

[stackalloc](stackalloc.md) -přiděluje blok paměti v zásobníku.

[->](pointer-related-operators.md#pointer-member-access-operator--) – dereferenci ukazatele v kombinaci s přístup ke členu.

## <a name="unary-operators"></a>Unární operátory

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[+ x](addition-operator.md) – vrátí hodnotu x.

[-x](subtraction-operator.md) – číselné negace.

[\!x](boolean-logical-operators.md#logical-negation-operator-) – Logická negace.

[~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitového doplňku.

[++ x](arithmetic-operators.md#increment-operator-) – předponového. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).

[--x](arithmetic-operators.md#decrement-operator---) – předponového. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).

[(T) x](type-testing-and-conversion-operators.md#cast-operator-) – typ přetypování.

[operátor await](../keywords/await.md) – čeká `Task`.

[& x](pointer-related-operators.md#address-of-operator-) – adresy proměnné.

[* x](pointer-related-operators.md#pointer-indirection-operator-) – dereferenci ukazatele nebo přístup přes ukazatel.

[True – – operátor](true-false-operators.md) – vrátí [bool](../keywords/bool.md) hodnotu `true` označuje jednoznačně true operand.

[false – – operátor](true-false-operators.md) – vrátí [bool](../keywords/bool.md) hodnotu `true` k označení, že operand je jednoznačně false.

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

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – posunutí bitů doleva a vyplnit nula na pravé straně.

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – posunutí bitů doprava. Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka. Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.

## <a name="relational-and-type-testing-operators"></a>Operátory relační a typové zkoušky

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x \< y](comparison-operators.md#less-than-operator-) – menší než (true, pokud x je menší než y).

[x > y](comparison-operators.md#greater-than-operator-) – větší než (true, pokud x je větší než y).

[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – menší než nebo rovno.

[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – větší než nebo rovna hodnotě.

[je](type-testing-and-conversion-operators.md#is-operator) – typ kompatibility. Vrátí `true` Pokud vyhodnocený levý operand může být převeden na typ určený pravého operandu.

[jako](type-testing-and-conversion-operators.md#as-operator) – převod typu. Vrátí levý operand přetypování na typ určený pravý operand, ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.

## <a name="equality-operators"></a>Operátory rovnosti

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x == y](equality-operators.md#equality-operator-) – rovnosti. Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test). Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.

[x! = y](equality-operators.md#inequality-operator-) – není rovno. Viz komentář `==`. Pokud typ přetížení `==`, pak musí přetížení `!=`.

## <a name="logical-and-operator"></a>Logický operátor AND

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

`x & y` – [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) pro `bool` operandy nebo [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) pro operandy integrální typy.

## <a name="logical-xor-operator"></a>Logický operátor XOR

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

`x ^ y` – [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) pro `bool` operandy nebo [bitové logické XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) pro operandy integrální typy.

## <a name="logical-or-operator"></a>Logický operátor OR

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

`x | y` – [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) pro `bool` operandy nebo [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) pro operandy integrální typy.

## <a name="conditional-and-operator"></a>Podmiňovací operátor AND

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – logickým operátorem a. Pokud `x` vyhodnotí jako `false`, pak `y` , nebude hodnocen.

## <a name="conditional-or-operator"></a>Podmiňovací operátor OR

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logický operátor OR. Pokud `x` vyhodnotí jako `true`, pak `y` , nebude hodnocen.

## <a name="null-coalescing-operator"></a>Operátoru nulového sjednocení

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x?? y](null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.

## <a name="conditional-operator"></a>Podmíněný operátor

Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.

[t? x: y](conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.

## <a name="assignment-and-lambda-operators"></a>Operátory přiřazení a lambda

Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.

[x = y](assignment-operator.md) – přiřazení.

[x += y](arithmetic-operators.md#compound-assignment) – přírůstku. Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu. Pokud `x` označí [události](../keywords/event.md), pak `y` musí být odpovídající metodu, která C# přidá jako obslužné rutiny události.

[x-= y](arithmetic-operators.md#compound-assignment) – sníží. Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu. Pokud `x` označí [události](../keywords/event.md), pak `y` musí být odpovídající metodu, která C# odebere jako obslužné rutiny události.

[x * = y](arithmetic-operators.md#compound-assignment) – přiřazení násobení. Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x / = y](arithmetic-operators.md#compound-assignment) – přiřazení dělení. Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.

[x % = y](arithmetic-operators.md#compound-assignment) – remainder přiřazení. Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.

[x & = y](boolean-logical-operators.md#compound-assignment) – a přiřazení. A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – přiřazení OR. NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x ^ = y](boolean-logical-operators.md#compound-assignment) – XOR přiřazení. XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.

[x << = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doleva. Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.

[x >> = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doprava. Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.

[=>](lambda-operator.md) – deklaraci lambda.

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory](../../programming-guide/statements-expressions-operators/operators.md)
