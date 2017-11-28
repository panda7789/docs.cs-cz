---
title: "Aritmetické operátory v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7fec98c38eebc34a0f84e051dc7c0914f537418f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operators-in-visual-basic"></a>Aritmetické operátory v jazyce Visual Basic
Aritmetické operátory slouží k provádění mnoha známé aritmetické operace, které zahrnují výpočet numerických hodnot reprezentována literály, proměnné, ostatní výrazy, funkce a vlastnosti volání a konstanty. Bitové posunutí – operátory, které fungují na úrovni jednotlivých bity operandy a jejich vzory bitové posunutí doleva nebo doprava taky klasifikované s aritmetické operátory jsou.  
  
## <a name="arithmetic-operations"></a>Aritmetické operace  
 Můžete přidat dvě hodnoty ve výrazu společně s [+ – operátor](../../../../visual-basic/language-reference/operators/addition-operator.md), nebo odečtena z jednoho do jiného s [– operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#57](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_1.vb)]  
  
 Negace používá také [– operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ale pouze jediný operand jako následující příklad ukazuje.  
  
 [!code-vb[VbVbalrOperators#58](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_2.vb)]  
  
 Použití násobení a dělení [* operátor](../../../../visual-basic/language-reference/operators/multiplication-operator.md) a [/ – operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md), respektive, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#59](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_3.vb)]  
  
 Exponenciální zápis používá [^ – operátor](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#60](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_4.vb)]  
  
 Celočíselné dělení probíhá pomocí [\ – operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Celočíselné dělení vrátí podílu, který je celé číslo představující počet, kolikrát dělitel lze rozdělit do dělenec bez ohledu na všechny zbývající. Celočíselné typy musí být dělitel i dělenec (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, a `ULong`) pro tento operátor. Všechny ostatní typy, musí být nejprve převést na typ integrální. Následující příklad ukazuje dělení celého čísla.  
  
 [!code-vb[VbVbalrOperators#61](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_5.vb)]  
  
 Aritmetické numerického zbytku se provádí pomocí [Mod operátor](../../../../visual-basic/language-reference/operators/mod-operator.md). Tento operátor Vrátí zbytek po dělení dělitel do dělenec integrální stanovený počet. Pokud dělitel i dělenec integrální typy, vrácená hodnota je nedílnou součástí. Pokud dělitel a dělenec jsou typy s plovoucí desetinnou čárkou, je také vrácené hodnoty s plovoucí desetinnou čárkou. Následující příklad ukazuje, toto chování.  
  
 [!code-vb[VbVbalrOperators#62](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_6.vb)]  
  
 [!code-vb[VbVbalrOperators#63](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_7.vb)]  
  
### <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Dělení nulou má odlišné výsledky v závislosti na zahrnutých datové typy. V integrální rozdělení (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyvolá <xref:System.DivideByZeroException> výjimka. V operacích dělení na `Decimal` nebo `Single` datového typu, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] také vyvolá <xref:System.DivideByZeroException> výjimka.  
  
 V souvisejících s plovoucí desetinnou čárkou rozdělení `Double` datového typu, nedojde k výjimce a výsledkem je člen třídy představující <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, nebo <xref:System.Double.NegativeInfinity>, v závislosti na dělenec. Následující tabulka shrnuje různé výsledky pokusu o rozdělení `Double` hodnotu nulou.  
  
|Dělenec datový typ|Dělitel datový typ|Hodnota dělenec|Výsledek|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(není matematicky určené číslo)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Když catch <xref:System.DivideByZeroException> výjimky, můžete použít její členy můžete ji zpracovat. Například <xref:System.Exception.Message%2A> vlastnost obsahuje text zprávy pro výjimku. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Bitové posunutí – operace  
 Bitové posunutí – operace provede aritmetický posun bitový. Vzor je součástí operand na levé straně, zatímco operand na pravé straně určuje počet pozic, který má posunutí vzoru. Vzor můžete posunutí doprava s [>> operátor](../../../../visual-basic/language-reference/operators/right-shift-operator.md) nebo vlevo s [<< operátor](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Datový typ operandu vzor musí být `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`. Datový typ operandu shift velikost musí být `Integer` nebo musí rozšířit pro `Integer`.  
  
 Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci. Pozice bit uprázdnili shift nastavené takto:  
  
-   0 pro aritmetické posunutí doleva  
  
-   0 pro aritmetické posunutí doprava o kladné číslo.  
  
-   0 pro aritmetické posunutí doprava bez znaménka datový typ. (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
-   1 pro aritmetické posunutí doprava záporná čísla (`SByte`, `Short`, `Integer`, nebo `Long`)  
  
 Následující příklad posune `Integer` hodnotu doleva a doprava.  
  
 [!code-vb[VbVbalrOperators#64](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/arithmetic-operators_8.vb)]  
  
 Aritmetické posuny nikdy generování výjimek přetečení.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Kromě toho logické operátory `Not`, `Or`, `And`, a `Xor` také provést bitové aritmetické při použití na číselné hodnoty. Další informace najdete v tématu "Bitový operací" v [logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Zabezpečení typů  
 Operandy by měl obvykle být stejného typu. Například, pokud byste přidávání pomocí `Integer` proměnné, měli byste přidat ho do jiného `Integer` proměnnou a měli přiřadit výsledek proměnné typu `Integer` také.  
  
 Jedním ze způsobů, aby funkční bezpečnost typů zvykem je použití [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Pokud nastavíte `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] automaticky provede *bezpečnost typů* převody. Například, pokud se pokusíte přidat `Integer` proměnnou `Double` proměnné a přiřazení hodnoty k `Double` proměnné, operace pokračuje normálně, protože `Integer` hodnotu lze převést na `Double` bez ztráty dat. Typ nezabezpečený převody na druhé straně způsobit chyby kompilátoru s `Option Strict On`. Například, pokud se pokusíte přidat `Integer` proměnnou `Double` proměnné a přiřaďte hodnota, která má `Integer` proměnné, Chyba kompilátoru výsledky, protože `Double` proměnnou nelze implicitně převést na typ `Integer`.  
  
 Pokud nastavíte `Option Strict Off`, ale [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] umožňuje implicitní zužující převody proběhla, i když může způsobit neočekávané dojít ke ztrátě dat nebo přesnosti. Z tohoto důvodu doporučujeme používat `Option Strict On` při zápisu produkčním kódu. Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Viz také  
 [Aritmetické operátory](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operátory bitového posunutí](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operátory řetězení v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
