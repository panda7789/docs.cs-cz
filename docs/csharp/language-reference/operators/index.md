---
title: "Operátory jazyka C#"
ms.date: 03/09/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ac5c6bfb129f0367c2d62ebf139e44b8eb60379
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="c-operators"></a>Operátory jazyka C#
C# poskytuje mnoho operátory, které jsou symboly, které určují, které operace (matematické, indexování, volání funkce atd.) provést ve výrazu.  Můžete [přetížení](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md) řada operátorů změnit jejich význam při aplikování uživatelem definovaného typu.  
  
 Operace u celočíselných typů (například `==`, `!=`, `<`, `>`, `&`, `|`) jsou obecně povolené na – výčet (`enum`) typy.  
  
 Části uvádí spouštění s nejvyšší prioritou nejnižší operátory jazyka C#.  Operátory v každém oddílu sdílet stejnou úroveň priority.  
  
## <a name="primary-operators"></a>Primární operátory  
 Jedná se o nejvyšší operátorů.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x.y](../../../csharp/language-reference/operators/member-access-operator.md) – přístup ke členu.  
  
 [x?. y](../../../csharp/language-reference/operators/null-conditional-operators.md) – null člen podmíněného přístupu.  Vrátí `null` Pokud levé operand `null`.  
 
 [x? [y] ](../../../csharp/language-reference/operators/null-conditional-operators.md) -null index podmíněného přístupu. Vrátí `null` Pokud levé operand `null`.
 
 [f(x)](../../../csharp/language-reference/operators/invocation-operator.md) – funkce volání.  
  
 [a &#91; x &#93; ](../../../csharp/language-reference/operators/index-operator.md) – agregovaný objekt indexování.  
   
 [x ++](../../../csharp/language-reference/operators/increment-operator.md) – přípony přírůstku.  Vrátí hodnotu x a pak aktualizuje umístění úložiště s hodnotou x, která je jeden znak větší (obvykle přidá na celé číslo 1).  
  
 [x –](../../../csharp/language-reference/operators/decrement-operator.md) – snížení přípony.  Vrátí hodnotu x a pak aktualizuje umístění úložiště s hodnotou x, který je jedním méně (obvykle odečítá celé číslo 1).  
  
 [nové](../../../csharp/language-reference/keywords/new-operator.md) – zadejte vytváření instancí.  
  
 [typeof](../../../csharp/language-reference/keywords/typeof.md) – vrátí System.Type objekt reprezentující operand.  
  
 [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) – umožňuje přetečení kontrola pro operace celé číslo.  
  
 [nezaškrtnuté](../../../csharp/language-reference/keywords/unchecked.md) – zakáže přetečení kontrola pro operace celé číslo.  Toto je výchozí chování kompilátoru.  
  
 [Default(T)](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md) – vrátí hodnotu výchozí typ T, `null` pro odkazové typy nula pro číselnými typy a nula nebo`null` vyplněno členy pro typy struktura.  
  
 [Delegovat](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) – deklaruje a vrátí instanci delegáta.  
  
 [sizeof –](../../../csharp/language-reference/keywords/sizeof.md) – vrátí velikost v bajtech operand typu.  
  
 [->](../../../csharp/language-reference/operators/dereference-operator.md)– ukazatel vyhodnocení v kombinaci s přístup ke členu.  
  
## <a name="unary-operators"></a>Unární operátory  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [+ x](../../../csharp/language-reference/operators/addition-operator.md) – vrátí hodnotu x.  
  
 [-x](../../../csharp/language-reference/operators/subtraction-operator.md) – číselné negace.  
  
 [! x](../../../csharp/language-reference/operators/logical-negation-operator.md) – logickou negaci.  
  
 [~ x](../../../csharp/language-reference/operators/bitwise-complement-operator.md) – bitového doplňku.  
  
 [++ x](../../../csharp/language-reference/operators/increment-operator.md) – předpona přírůstku.  Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, který je jedním větší (obvykle přidá na celé číslo 1).  
  
 [--x](../../../csharp/language-reference/operators/decrement-operator.md) – snížení předpony.  Vrátí hodnotu x po aktualizaci umístění úložiště s hodnotou x, který je jedním méně (obvykle přidá na celé číslo 1).  
  
 [(T) x](../../../csharp/language-reference/operators/invocation-operator.md) – typ přetypování.  
  
 [await](../../../csharp/language-reference/keywords/await.md) – čeká `Task`.  
  
 [& x](../../../csharp/language-reference/operators/and-operator.md) – adresu.  
  
 [* x](../../../csharp/language-reference/operators/multiplication-operator.md) – při přesměrování.  
  
## <a name="multiplicative-operators"></a>Operátory násobení  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x * y](../../../csharp/language-reference/operators/multiplication-operator.md) – násobení.  
  
 [x nebo y](../../../csharp/language-reference/operators/division-operator.md) – dělení.  Pokud operandy celá čísla, výsledkem je celé číslo, zkrátí směrem k nule (například `-7 / 2 is -3`).  
  
 [x, % y](../../../csharp/language-reference/operators/modulus-operator.md) – numerického zbytku.  Pokud operandy celých čísel, vrátí zbytek dělicí x y.  Pokud `q = x / y` a `r = x % y`, pak `x = q * y + r`.  
  
## <a name="additive-operators"></a>Operátory sčítání  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x a y](../../../csharp/language-reference/operators/addition-operator.md) – přidání.  
  
 [x – y](../../../csharp/language-reference/operators/subtraction-operator.md) – odčítání.  
  
## <a name="shift-operators"></a>Operátory posunutí  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x <\< y](../../../csharp/language-reference/operators/left-shift-operator.md) – posunutí doleva bits a vyplníte nula na pravé straně.  
  
 [x >> y](../../../csharp/language-reference/operators/right-shift-operator.md) – shift bitů doprava.  Pokud je levý operand `int` nebo `long`, pak levém bits jsou vyplněny bit přihlášení.  Pokud je levý operand `uint` nebo `ulong`, pak levém bits jsou vyplněny nula.  
  
## <a name="relational-and-type-testing-operators"></a>Relační a testování typ operátory  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x \< y](../../../csharp/language-reference/operators/less-than-operator.md) – menší než (hodnotu true, pokud x je menší než y).  
  
 [x > y](../../../csharp/language-reference/operators/greater-than-operator.md) – větší než (hodnotu true, pokud x je větší než y).  
  
 [x \<= y](../../../csharp/language-reference/operators/less-than-equal-operator.md) – menší než nebo rovna hodnotě.  
  
 [x > = y](../../../csharp/language-reference/operators/greater-than-equal-operator.md) – větší než nebo rovna hodnotě.  
  
 [je](../../../csharp/language-reference/keywords/is.md) – typ kompatibility.  Vrátí hodnotu true Pokud vyhodnotí levý operand lze převést na typ určený v pravý operand (statické typ).  
  
 [jako](../../../csharp/language-reference/keywords/as.md) – typ – převod.  Vrátí levý operand přetypovat na typ určený pravý operand (statické typu), ale `as` vrátí `null` kde `(T)x` by vyvolat výjimku.  
  
## <a name="equality-operators"></a>Operátory rovnosti  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x == y](../../../csharp/language-reference/operators/equality-comparison-operator.md) – rovnosti.  Ve výchozím nastavení, pro odkaz na typy jiné než `string`tento vrátí referenční rovnosti (identity test).  Však může přetížit typy `==`, takže pokud je otestovat identity vašich představ, je nejvhodnější použít `ReferenceEquals` metodu `object`.  
  
 [x! = y](../../../csharp/language-reference/operators/not-equal-operator.md) – není rovno.  Najdete v článku komentář pro `==`.  Pokud typ přetížení `==`, pak musí přetížení `!=`.  
  
## <a name="logical-and-operator"></a>Logický operátor AND  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [x a y](../../../csharp/language-reference/operators/and-operator.md) – logický operátor or bitové operátorem a.  Použití s typy celého čísla a `enum` obecně povolené typy.  
  
## <a name="logical-xor-operator"></a>Logické XOR – operátor  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [x ^ y](../../../csharp/language-reference/operators/xor-operator.md) – logickou nebo bitové operace XOR.  To můžete obvykle použít s typy celého čísla a `enum` typy.  
  
## <a name="logical-or-operator"></a>Logický operátor OR  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [x &#124; y](../../../csharp/language-reference/operators/or-operator.md) – logickou nebo bitové operace OR.  Použití s typy celého čísla a `enum` obecně povolené typy.  
  
## <a name="conditional-and-operator"></a>Operátor podmíněného AND  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [x & & y](../../../csharp/language-reference/operators/conditional-and-operator.md) – logickým operátorem a.  Pokud je první operand false, pak C# nevyhodnocuje Druhý operand.  
  
## <a name="conditional-or-operator"></a>Podmíněný operátor OR  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [x &#124; &#124; y](../../../csharp/language-reference/operators/conditional-or-operator.md) – logické OR.  Je-li první operand hodnotu true, pak C# nevyhodnocuje Druhý operand.  
  
## <a name="null-coalescing-operator"></a>Slučování Null – operátor  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [x?? y](../../../csharp/language-reference/operators/null-conditional-operator.md) – vrátí `x` Pokud je jinou hodnotu než`null`, jinak vrátí `y`.  
  
## <a name="conditional-operator"></a>Podmíněný operátor  
 Tento operátor má vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátor přejdete na stránku podrobností s příklady.  
  
 [t? x: y](../../../csharp/language-reference/operators/conditional-operator.md) – Pokud testování `t` je true, pak vyhodnotí a vrátí `x`; jinak vyhodnotit a vrátí `y`.  
  
## <a name="assignment-and-lambda-operators"></a>Přiřazení a operátory Lambda  
 Tyto operátory mají vyšší prioritu než v další části a nižší prioritu než předchozí části.  Všimněte si, že se můžete kliknutím na operátory přejít na podrobných stránkách s příklady.  
  
 [x = y](../../../csharp/language-reference/operators/assignment-operator.md) – přiřazení.  
  
 [x += y](../../../csharp/language-reference/operators/addition-assignment-operator.md) – přírůstku.  Přidejte hodnotu `y` na hodnotu `x`, uložit výsledek v `x`a vrátí novou hodnotu.  Pokud `x` označí `event`, pak `y` musí být odpovídající funkce, která C# přidává jako obslužnou rutinu události.  
  
 [x-= y](../../../csharp/language-reference/operators/subtraction-assignment-operator.md) – snížení.  Odečíst hodnotu `y` od hodnoty `x`, uložit výsledek v `x`a vrátí novou hodnotu.  Pokud `x` označí `event`, pak `y` příslušnou funkci, která C# odebere jako obslužné rutiny události musí být.  
  
 [x * = y](../../../csharp/language-reference/operators/multiplication-assignment-operator.md) – přiřazení násobení.  Vynásobit hodnoty `y` na hodnotu `x`, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [x / = y](../../../csharp/language-reference/operators/division-assignment-operator.md) – přiřazení dělení.  Rozdělení hodnota `x` hodnotou `y`, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [x % = y](../../../csharp/language-reference/operators/modulus-assignment-operator.md) – přiřazení numerického zbytku.  Rozdělení hodnota `x` hodnotou `y`, uložení zbývající v `x`a vrátí novou hodnotu.  
  
 [x & = y](../../../csharp/language-reference/operators/and-assignment-operator.md) – a přiřazení.  A hodnotu `y` s hodnotou `x`, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [x &#124; = y](../../../csharp/language-reference/operators/or-assignment-operator.md) – přiřazení OR.  NEBO hodnota `y` s hodnotou `x`, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [x ^ = y](../../../csharp/language-reference/operators/xor-assignment-operator.md) – XOR přiřazení.  XOR hodnotu z `y` s hodnotou `x`, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [x << = y](../../../csharp/language-reference/operators/left-shift-assignment-operator.md) – přiřazení posunutí doleva.  Hodnota posunutí `x` vlevo po `y` místech, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [x >> = y](../../../csharp/language-reference/operators/right-shift-assignment-operator.md) – přiřazení posunutí doprava.  Hodnota posunutí `x` přímo pomocí `y` místech, uložit výsledek v `x`a vrátí novou hodnotu.  
  
 [=>](../../../csharp/language-reference/operators/lambda-operator.md)– deklarace lambda.  
  
## <a name="arithmetic-overflow"></a>Aritmetického přetečení  
 Aritmetické operátory ([+](../../../csharp/language-reference/operators/addition-operator.md), [ - ](../../../csharp/language-reference/operators/subtraction-operator.md), [ * ](../../../csharp/language-reference/operators/multiplication-operator.md), [ / ](../../../csharp/language-reference/operators/division-operator.md)) může nepřineslo výsledky, které jsou mimo rozsah možných hodnot pro číselné typ související se situací. Naleznete v části na konkrétní operátor podrobnosti, ale obecně:  
  
- Celočíselné aritmetiky přetečení buď vyvolává <xref:System.OverflowException> nebo zahodí nejvýznamnějších bits výsledku. Celočíselné dělení podle nula vždycky vyvolává <xref:System.DivideByZeroException>.  

   Když dojde k přetečení celé číslo, co se stane, závisí na kontext spuštění, který může být [zaškrtnuté nebo nezaškrtnuté](../../../csharp/language-reference/keywords/checked-and-unchecked.md). V kontextu zaškrtnuté <xref:System.OverflowException> je vyvolána výjimka. V kontextu není zaškrtnuto jsou zahozeny nejvýznamnějších bits výsledku a pokračuje v provádění. Proto C# vám dává možnost zpracování nebo ignoruje přetečení. Ve výchozím nastavení, dojde k aritmetické operace v *nezaškrtnuté* kontextu. 

   Kromě aritmetické operace přetypování typ celé číslo na celé číslo – typu může způsobit přetečení (například když přetypovat [dlouho](../../../csharp/language-reference/keywords/long.md) k [int](../../../csharp/language-reference/keywords/int.md)) a podléhají provádění zaškrtnuté nebo nezaškrtnuté. Ale bitové operátory a operátory posunutí nikdy způsobit přetečení.  
   
-   S plovoucí desetinnou čárkou aritmetického přetečení nebo dělení nulou nikdy vyvolá výjimku, protože typy s plovoucí desetinnou čárkou jsou založené na standardu IEEE 754 a tak mít zřizuje představující infinity a NaN (není číslo).  
  
-   [Decimal](../../../csharp/language-reference/keywords/decimal.md) aritmetického přetečení vždy vyvolá <xref:System.OverflowException>. Decimal dělení nula vždycky vyvolává <xref:System.DivideByZeroException>.  
  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md) [přetížitelné operátory](../../../csharp/programming-guide/statements-expressions-operators/overloadable-operators.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
