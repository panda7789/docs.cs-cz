---
title: Operátory jazyka C#
ms.date: 04/04/2018
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
ms.openlocfilehash: 2b0441dfebb6692cbea0d1ab7909d7b8f04490cb
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "34457601"
---
# <a name="c-operators"></a>Operátory jazyka C#
Jazyk C# poskytuje mnoho operátorů, které jsou symboly, které určují operace, které (matematické, indexování, volání funkce atd.) provést ve výrazu. Je možné [přetížení](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) mnoho operátorů, chcete-li změnit jejich význam při aplikování na uživatelem definovaného typu.  
  
 Operace interních typů (například `==`, `!=`, `<`, `>`, `&`, `|`) jsou obecně povoleny na výčet (`enum`) typy.  
  
 Níže uvedených částech najdete seznam operátorů jazyka C# od nejvyšší prioritu, takže nejnižší. Operátory v jednotlivých částech sdílet stejnou úrovní priority.  
 
## <a name="primary-operators"></a>Primární operátory  
 Jedná se o nejvyšší priorita operátorů.
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – přístup ke členu.  
  
 [x?. y](../../../csharp/language-reference/operators/null-conditional-operators.md) – přístup Podmíněný člen s hodnotou null. Vrátí `null` pokud levý operand je vyhodnocen jako `null`.  
 
 [x? [y] ](../../../csharp/language-reference/operators/null-conditional-operators.md) -index podmíněného přístupu s hodnotou null. Vrátí `null` pokud levý operand je vyhodnocen jako `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – funkce volání.  
  
 [&#91;x&#93; ](../../../csharp/language-reference/operators/index-operator.md) – indexování agregovaný objekt.  
   
 [x ++](../../../csharp/language-reference/operators/increment-operator.md) – Příponové operátory Inkrementace. Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden znak větší (obvykle přidá na celé číslo 1).  
  
 [x--](../../../csharp/language-reference/operators/decrement-operator.md) – snížení příponového operátora. Vrací hodnotu x a následně aktualizuje umístění úložiště hodnota x je jeden méně (obvykle odečte 1 na celé číslo).  
  
 [nové](../../../csharp/language-reference/keywords/new-operator.md) – typ vytváření instancí.  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) – vrátí <xref:System.Type> objekt představující operand.  
  
 [checked](../../../csharp/language-reference/keywords/checked.md) – umožňuje pro celočíselné operace kontroly přetečení.  
  
 [unchecked](../../../csharp/language-reference/keywords/unchecked.md) – zakáže pro celočíselné operace kontroly přetečení. Toto je výchozí chování kompilátoru.  
  
 [Default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – vytvoří výchozí hodnotu typu T.  
  
 [Delegovat](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.  
  
 [operátor sizeof:](../../../csharp/language-reference/keywords/sizeof.md) – vrátí velikost v bajtech typ operandu.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md) – přístup přes ukazatel v kombinaci s přístup ke členu.  
  
## <a name="unary-operators"></a>Unární operátory  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [+ x](../../../csharp/language-reference/operators/addition-operator.md) – vrátí hodnotu x.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) – číselné negace.  
  
 [\!x](../../../csharp/language-reference/operators/logical-negation-operator.md) – Logická negace.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – bitového doplňku.  
  
 [++ x](../../../csharp/language-reference/operators/increment-operator.md) – předponového. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, která je větší (obvykle přidá na celé číslo 1).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) – předponového. Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x je jeden méně (obvykle odečte 1 na celé číslo).  
  
 [(T) x](../../../csharp/language-reference/operators/invocation-operator.md) – typ přetypování.  
  
 [operátor await](../../../csharp/language-reference/keywords/await.md) – čeká `Task`.  
  
 [& x](../../../csharp/language-reference/operators/and-operator.md) – adresu.  
  
 [* x](../../../csharp/language-reference/operators/multiplication-operator.md) – přesměrování.  
  
## <a name="multiplicative-operators"></a>Operátory násobení  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) – násobení.  
  
 [x a y](../../../csharp/language-reference/operators/division-operator.md) – dělení. Pokud jsou operandy celých čísel, výsledek je celé číslo zkráceno směrem k nule (například `-7 / 2 is -3`).  
  
 [x, % y](../../../csharp/language-reference/operators/remainder-operator.md) – zbytek. Pokud jsou operandy celých čísel, vrátí zbytek dělicí x y.  Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.  
  
## <a name="additive-operators"></a>Operátory sčítání  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x + y](../../../csharp/language-reference/operators/addition-operator.md) – přidání.  
  
 [x-y](../../../csharp/language-reference/operators/subtraction-operator.md) – odčítání.  
  
## <a name="shift-operators"></a>Operátory posunutí  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) – posunutí bitů doleva a vyplnit nula na pravé straně.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – posunutí bitů doprava. Pokud levý operand `int` nebo `long`, pak levé bity jsou vyplněny na bit znaménka. Pokud levý operand `uint` nebo `ulong`, pak levé bity jsou vyplněny hodnotou nula.  
  
## <a name="relational-and-type-testing-operators"></a>Operátory relační a typové zkoušky  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – menší než (true, pokud x je menší než y).  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – větší než (true, pokud x je větší než y).  
  
 [x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – menší než nebo rovno.  
  
 [x > = y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – větší než nebo rovna hodnotě.  
  
 [je](../../../csharp/language-reference/keywords/is.md) – typ kompatibility. Vrátí true, pokud vyhodnocený levý operand může být převeden na typ určený v pravý operand (statického typu).  
  
 [jako](../../../csharp/language-reference/keywords/as.md) – převod typu. Vrátí levý operand přetypování na typ určený pravý operand (statického typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.  
  
## <a name="equality-operators"></a>Operátory rovnosti  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – rovnosti. Ve výchozím nastavení, pro referenční typy jiné než `string`tento vrátí referenční rovnosti (identity test). Však můžete přetížit typy `==`, takže pokud máte v úmyslu k otestování identity, je nejvhodnější použít `ReferenceEquals` metodu na `object`.  
  
 [x! = y](../../../csharp/language-reference/operators/not-equal-operator.md) – není rovno. Viz komentář `==`. Pokud typ přetížení `==`, pak musí přetížení `!=`.  
  
## <a name="logical-and-operator"></a>Logický operátor AND  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x & y](../../../csharp/language-reference/operators/and-operator.md) – logický operátor or bitový AND. Obecně můžete s celočíselnými typy a `enum` typy.  
  
## <a name="logical-xor-operator"></a>Logický operátor XOR – operátor  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – logické a bitové operace XOR. Obecně můžete s celočíselnými typy a `enum` typy.  
  
## <a name="logical-or-operator"></a>Logický operátor OR  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – logické a bitové operace OR. Obecně můžete s celočíselnými typy a `enum` typy.  
  
## <a name="conditional-and-operator"></a>Operátor podmíněného AND  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) – logickým operátorem a. Pokud je první operand vyhodnocen na hodnotu false, pak C# není vyhodnocen Druhý operand.  
  
## <a name="conditional-or-operator"></a>Podmíněný operátor OR  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – logický operátor OR. Pokud je první operand vyhodnocen na hodnotu true, pak C# není vyhodnocen Druhý operand.  
  
## <a name="null-coalescing-operator"></a>Operátoru nulového sjednocení  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x?? y](../../../csharp/language-reference/operators/null-coalescing-operator.md) – vrátí `x` jde-li jinou hodnotu než`null`; v opačném případě vrátí `y`.  
  
## <a name="conditional-operator"></a>Podmíněný operátor  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) – Pokud test `t` vyhodnotí jako true, pak vyhodnotí a vrátí `x`; v opačném případě vyhodnotí a vrátí `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Přiřazení a Lambda operátorů  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) – přiřazení.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – přírůstku. Přidat hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu. Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# přidá jako obslužné rutiny události.  
  
 [x-= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – sníží. Odečte hodnotu `y` od hodnoty `x`, uloží výsledek v `x`a vrátí novou hodnotu. Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# odebere jako obslužné rutiny události  
  
 [x * = y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – přiřazení násobení. Vynásobí hodnotu `y` hodnotě `x`, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [x / = y](../../../csharp/language-reference/operators/division-assignment-operator.md) – přiřazení dělení. Vydělí hodnotu `x` hodnotou `y`, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [x % = y](../../../csharp/language-reference/operators/remainder-assignment-operator.md) – remainder přiřazení. Vydělí hodnotu `x` hodnotou `y`, uložení zbytku v `x`a vrátí novou hodnotu.  
  
 [x & = y](../../../csharp/language-reference/operators/and-assignment-operator.md) – a přiřazení. A hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [x &#124;= y](../../../csharp/language-reference/operators/or-assignment-operator.md) – přiřazení OR. NEBO hodnota `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [x ^ = y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR přiřazení. XOR hodnotu z `y` s hodnotou `x`, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [x << = y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – přiřazení posunutí doleva. Posune hodnotu `x` vlevo po `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [x >> = y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – přiřazení posunutí doprava. Posune hodnotu `x` právo `y` místech, uloží výsledek v `x`a vrátí novou hodnotu.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md) – deklaraci lambda.  
  
## <a name="arithmetic-overflow"></a>Aritmetické přetečení  
 Aritmetické operátory ([+](../../../csharp/language-reference/operators/addition-operator.md), [ - ](../../../csharp/language-reference/operators/subtraction-operator.md), [ * ](../../../csharp/language-reference/operators/multiplication-operator.md), [ / ](../../../csharp/language-reference/operators/division-operator.md)) může výsledky, které jsou mimo rozsah možných hodnot pro uvedeného číselného typu. By měla odkazovat na část na konkrétní operátor podrobnosti, ale obecně:  
  
- Aritmetické přetečení celého čísla buď vyvolá <xref:System.OverflowException> nebo zruší nejvýznamnější části výsledku. Dělení celého čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.  

   Pokud dojde k přetečení celého čísla, co se stane, závisí na kontextu spuštění, který může být [zaškrtnuté nebo nezaškrtnuté](../../../csharp/language-reference/keywords/checked-and-unchecked.md). Ve zkontrolovaném kontextu <xref:System.OverflowException> je vyvolána výjimka. V nekontrolovaném kontextu jsou nejvýznamnější části výsledku ignorovány a provádění bude pokračovat. Proto jazyk C# umožňuje volbu zpracování nebo ignorování přetečení. Ve výchozím nastavení, aritmetické operace prováděny v *Nekontrolovaná* kontextu. 

   Kromě aritmetických operací, přetypování integrálového typu na integrálový typ může způsobit přetečení (jako je například, pokud přetypovat [dlouhé](../../../csharp/language-reference/keywords/long.md) do [int](../../../csharp/language-reference/keywords/int.md)) a můžou se nekontrolovaným prováděním. Nicméně bitové operátory a operátory posunutí nikdy nezpůsobí přetečení.  
   
-   Plovoucí aritmetické přetečení nebo dělení nulou nikdy nevyvolá výjimku, protože typy s plovoucí desetinnou čárkou jsou založeny na standardu IEEE 754 a tak mají opatření představující nekonečno a NaN (není číslo).  
  
-   [Desetinné](../../../csharp/language-reference/keywords/decimal.md) aritmetické přetečení vždy vyvolá <xref:System.OverflowException>. Dělení desetinného čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [přetížitelné operátory](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
