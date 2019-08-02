---
title: C#operátory – C# referenční informace
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
ms.openlocfilehash: 13ad16ab768cdaee96cab29811e2ed058dee977a
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512243"
---
# <a name="c-operators-c-reference"></a>C#operátory (C# Referenční dokumentace)

C#poskytuje několik předdefinovaných operátorů podporovaných integrovanými typy. Například aritmetické [operátory](arithmetic-operators.md) provádějí aritmetické operace s operandy předdefinovaných číselných typů a logické [logické operátory](boolean-logical-operators.md) provádějí logické operace s logickými [operandy](../keywords/bool.md) .

Uživatelsky definovaný typ může přetížit určité operátory pro definování odpovídajícího chování pro operandy daného typu. Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).

V následujících částech jsou uvedeny C# operátory začínající nejvyšší prioritou na nejnižší. Operátory v jednotlivých oddílech sdílí stejnou úroveň priority.

## <a name="primary-operators"></a>Primární operátory

Toto jsou operátory s nejvyšší prioritou.

[x. y](member-access-operators.md#member-access-operator-) – přístup ke členu

[x?. y](member-access-operators.md#null-conditional-operators--and-) – null přístup podmíněného člena. Vrátí `null` , zda je na levé straně operand vyhodnocen `null`.

[x? [y]](member-access-operators.md#null-conditional-operators--and-) – podmíněný element pole nebo typ přístupu indexeru typu null. Vrátí `null` , zda je na levé straně operand vyhodnocen `null`.

[f (x)](member-access-operators.md#invocation-operator-) – volání metody nebo volání delegáta.

přístup k elementu [&#91;x&#93; ](member-access-operators.md#indexer-operator-) -Array nebo k indexeru typů.

[x + +](arithmetic-operators.md#increment-operator-) – přírůstek přípony Vrátí hodnotu x a poté aktualizuje umístění úložiště hodnotou x, která je jedna větší (obvykle přidá celé číslo 1).

[x--](arithmetic-operators.md#decrement-operator---) – – snížení přípony Vrátí hodnotu x a poté aktualizuje umístění úložiště hodnotou x, která je menší (obvykle se odečte celé číslo 1).

[nové](new-operator.md) – vytvoření instance typu.

[typeof](type-testing-and-conversion-operators.md#typeof-operator) – vrátí <xref:System.Type> objekt představující operand.

[checked](../keywords/checked.md) – povolí kontrolu přetečení pro celočíselné operace.

[nezaškrtnuto](../keywords/unchecked.md) – zakáže kontrolu přetečení pro celočíselné operace. Toto je výchozí chování kompilátoru.

[Default (T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.

[nameof](nameof.md) – získá jednoduchý (nekvalifikovaný) název proměnné, typu nebo členu jako konstantní řetězec.

[Delegate](delegate-operator.md) – deklaruje a vrátí instanci delegáta.

[sizeof](sizeof.md) – vrátí velikost operandu typu v bajtech.

[stackalloc](stackalloc.md) – přidělí blok paměti v zásobníku.

[->](pointer-related-operators.md#pointer-member-access-operator--)– nepřímý odkaz v kombinaci s přístupem členů.

## <a name="unary-operators"></a>Unární operátory

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[+ x](addition-operator.md) – vrátí hodnotu x.

[-x](subtraction-operator.md) – číselná negace.

x – logická negace. [ \!](boolean-logical-operators.md#logical-negation-operator-)

[~ ×](bitwise-and-shift-operators.md#bitwise-complement-operator-) – bitový doplněk.

[+ + x](arithmetic-operators.md#increment-operator-) – přírůstek předpony. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je jedna větší (obvykle přidá celé číslo 1).

[--x](arithmetic-operators.md#decrement-operator---) – snížení předpony. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je o jednu méně (obvykle odečte celé číslo 1).

[(T) x](type-testing-and-conversion-operators.md#cast-operator-) – přetypování typu.

[await](../keywords/await.md) – čeká na `Task`.

[& x](pointer-related-operators.md#address-of-operator-) – adresa proměnné.

[* x](pointer-related-operators.md#pointer-indirection-operator-) – indirekce ukazatele nebo přereference.

[true – operátor](true-false-operators.md) – vrátí [](../keywords/bool.md) logickou `true` hodnotu pro indikaci, že operand má jednoznačně hodnotu true.

[false – operátor](true-false-operators.md) – vrátí [](../keywords/bool.md) logickou `true` hodnotu pro indikaci, že operand je jednoznačně nepravdivý.

## <a name="multiplicative-operators"></a>Operátory násobení

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x * y](arithmetic-operators.md#multiplication-operator-) – násobení.

[x/y](arithmetic-operators.md#division-operator-) – dělení. Pokud jsou operandy celé číslo, výsledkem je celé číslo, které je zkráceno směrem k nule ( `-7 / 2 is -3`například).

[x% y](arithmetic-operators.md#remainder-operator-) – zbytek Pokud jsou operandy celé číslo, vrátí zbytek dělení x hodnotou y.  Pokud `q = x / y` a `r = x % y`, potom `x = q * y + r`.

## <a name="additive-operators"></a>Operátory sčítání

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x + y](arithmetic-operators.md#addition-operator-) – přidání.

[x – y](arithmetic-operators.md#subtraction-operator--) – odčítání.

## <a name="shift-operators"></a>Operátory posunutí

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x <\< y](bitwise-and-shift-operators.md#left-shift-operator-) – klávesy SHIFT vlevo a na pravé straně se vyplní nula.

[x > > y](bitwise-and-shift-operators.md#right-shift-operator-) – Shift + šipka doprava. Pokud je `int` levý operand nebo `long`, pak jsou levé bity vyplněny znaménkem. Pokud je `uint` levý operand nebo `ulong`, pak jsou levé bity vyplněny nulou.

## <a name="relational-and-type-testing-operators"></a>Relační operátory a operátory testování typů

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[ x\< y](comparison-operators.md#less-than-operator-) – menší než (true, pokud je x menší než y).

[x > y](comparison-operators.md#greater-than-operator-) – větší než (true, pokud je x větší než y).

[ x\<= y](comparison-operators.md#less-than-or-equal-operator-) – je menší nebo rovno.

[x > = y](comparison-operators.md#greater-than-or-equal-operator-) – je větší než nebo rovno.

[je](type-testing-and-conversion-operators.md#is-operator) – kompatibilita typů. Vrátí `true` , zda je možné vyhodnocený levý operand přetypovat na typ zadaný pomocí pravého operandu.

převod [jako](type-testing-and-conversion-operators.md#as-operator) – typ. Vrátí levý operand přetypování na typ určený pravý operandem, ale `as` vrátí `null` , kde `(T)x` by vyvolala výjimku.

## <a name="equality-operators"></a>Operátory rovnosti

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x = = y](equality-operators.md#equality-operator-) – rovnost. Ve výchozím nastavení pro jiné typy odkazů než `string`, tato funkce vrátí rovnost odkazů (test identity). Typy však mohou přetížit `==`, takže pokud je váš záměr testovat identitu, je nejvhodnější `ReferenceEquals` použít metodu na `object`.

[x! = y](equality-operators.md#inequality-operator-) – nerovná se Viz komentář pro `==`. Je-li typ přetížen `==`, je nutné jej přetížit. `!=`

## <a name="logical-and-operator"></a>Logický operátor AND

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

`x & y`– [logická a](boolean-logical-operators.md#logical-and-operator-) pro `bool` operandy nebo [bitové logické a](bitwise-and-shift-operators.md#logical-and-operator-) pro operandy integrálních typů.

## <a name="logical-xor-operator"></a>Logický operátor XOR

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

`x ^ y`– [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) pro `bool` operandy nebo [bitové logické XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) pro operandy integrálních typů.

## <a name="logical-or-operator"></a>Logický operátor OR

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

`x | y`– [logická nebo](boolean-logical-operators.md#logical-or-operator-) pro `bool` operandy nebo [bitové logické číslo nebo](bitwise-and-shift-operators.md#logical-or-operator-) pro operandy integrálních typů.

## <a name="conditional-and-operator"></a>Podmíněný operátor AND

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) – Logical a. Pokud `x` se vyhodnotí `false`jako `y` , pak se nevyhodnotí.

## <a name="conditional-or-operator"></a>Podmíněný operátor OR

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[ &#124; x &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – logická nebo. Pokud `x` se vyhodnotí `true`jako `y` , pak se nevyhodnotí.

## <a name="null-coalescing-operator"></a>Operátor slučování null

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x?? y](null-coalescing-operator.md) – vrátí `x` , pokud je`null`to jiné než; v opačném případě vrátí `y`.

## <a name="conditional-operator"></a>Podmíněný operátor

Tento operátor má vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[t? x: y](conditional-operator.md) – Pokud se `t` test vyhodnotí jako true, pak se `x`vyhodnotí a vrátí. `y`jinak se vyhodnotí a vrátí.

## <a name="assignment-and-lambda-operators"></a>Operátory přiřazení a lambda

Tyto operátory mají vyšší prioritu než další oddíl a nižší prioritu než předchozí oddíl.

[x = y](assignment-operator.md) – přiřazení.

[x + = y](arithmetic-operators.md#compound-assignment) – přírůstek Přidejte hodnotu `y` do `x`hodnoty, uložte výsledek do `x`a vraťte novou hodnotu. Pokud `x` Určuje C# [událost, musí být](../keywords/event.md)vhodná metoda, která je přidána jako obslužná rutina události. `y`

[x-= y](arithmetic-operators.md#compound-assignment) – snížení. Odečte hodnotu `y` z `x`hodnoty, uloží výsledek do `x`a vrátí novou hodnotu. Pokud `x` Určuje C# [událost, musí být](../keywords/event.md)vhodná metoda, která se odebere jako obslužná rutina události. `y`

[x * = y](arithmetic-operators.md#compound-assignment) – přiřazení násobení. Vynásobte hodnotu `y` `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.

přiřazení divize [x/= y](arithmetic-operators.md#compound-assignment) – dělení. Vydělte hodnotu `x` `y`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.

[x% = y](arithmetic-operators.md#compound-assignment) – přiřazení zbytku Vydělte hodnotu `x` `y`hodnotou, uložte zbytek do `x`a vraťte novou hodnotu.

[x & = y](boolean-logical-operators.md#compound-assignment) – a přiřazení. A hodnotu `y` s `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – nebo přiřazení. Nebo hodnotu `y` s `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.

[x ^ = y](boolean-logical-operators.md#compound-assignment) – přiřazení XOR XOR hodnotu `y` s `x`hodnotou, uložte výsledek do `x`a vraťte novou hodnotu.

[x < < = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doleva. Posune hodnotu `x` vlevo o `y` místa, uloží výsledek do `x`a vrátí novou hodnotu.

[x > > = y](bitwise-and-shift-operators.md#compound-assignment) – přiřazení posunutí doprava. Posune hodnotu `x` vpravo podle `y` míst, uloží výsledek do `x`a vrátí novou hodnotu.

[=>](lambda-operator.md)– deklarace lambda

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory](../../programming-guide/statements-expressions-operators/operators.md)
