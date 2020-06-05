---
title: Aritmetické operátory
ms.date: 07/20/2015
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
ms.openlocfilehash: d5f79f3e45fc887dcb32c959f04703253ade198c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389033"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Aritmetické operátory v jazyce Visual Basic
Aritmetické operátory slouží k provádění mnoha známých aritmetických operací, které zahrnují výpočet numerických hodnot reprezentovaných literály, proměnnými, ostatními výrazy, volání funkcí a vlastností a konstantami. Klasifikovaný s aritmetickými operátory jsou také operátory bitového posunutí, které působí na úrovni jednotlivých bitů operandů a posunují své bitové vzory doleva nebo doprava.  
  
## <a name="arithmetic-operations"></a>Aritmetické operace  
 Do výrazu můžete přidat dvě hodnoty společně s [operátorem +](../../../language-reference/operators/addition-operator.md)nebo odečíst jeden z druhý s [operátorem--operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Negace také používá [operátor-(Visual Basic)](../../../language-reference/operators/subtraction-operator.md), ale pouze jeden operand, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Násobení a dělení používají [operátor *](../../../language-reference/operators/multiplication-operator.md) a operátor [(Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Exponent používá [operátor ^](../../../language-reference/operators/exponentiation-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Dělení celého čísla je prováděno pomocí [operátoru \ (Visual Basic)](../../../language-reference/operators/integer-division-operator.md). Celočíselná celočíselná hodnota vrátí podíl, tj. celé číslo, které představuje počet pokusů, které může dělitel rozdělit na dividendy bez zvážení zbytku. Dělitel i dividenda musí být `SByte` pro tento operátor integrální typy (, `Byte` , `Short` , `UShort` , `Integer` ,, a `UInteger` `Long` `ULong` ). Všechny ostatní typy musí být nejprve převedeny na celočíselný typ. Následující příklad ukazuje celočíselné dělení.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 Aritmetické moduly jsou prováděny pomocí [operátoru mod](../../../language-reference/operators/mod-operator.md). Tento operátor vrátí zbytek po dělení dělitele do dividendy integrálního čísla. Pokud jsou dělitel i dividendy integrálních typů, vrácená hodnota je celočíselná. Pokud jsou dělitel a dividendy typy s plovoucí desetinnou čárkou, vrácená hodnota je také plovoucí desetinná čárka. Následující příklad demonstruje toto chování.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Došlo k pokusu o dělení nulou.  
 Dělení nulou má různé výsledky v závislosti na typech dat, které se týkají. V celočíselném dělení ( `SByte` , `Byte` ,, `Short` `UShort` , `Integer` , `UInteger` , `Long` , `ULong` ) .NET Framework vyvolá <xref:System.DivideByZeroException> výjimku. V rámci dělení operací `Decimal` nebo `Single` datového typu .NET Framework vyvolá také <xref:System.DivideByZeroException> výjimku.  
  
 V divizích s plovoucí desetinnou čárkou, které zahrnují `Double` datový typ, není vyvolána žádná výjimka a výsledkem je člen třídy, který představuje <xref:System.Double.NaN> , <xref:System.Double.PositiveInfinity> nebo <xref:System.Double.NegativeInfinity> , v závislosti na dividendě. Následující tabulka shrnuje různé výsledky pokusu o rozdělení `Double` hodnoty nulou.  
  
|Datový typ dividendy|Dělitel – datový typ|Hodnota dividendy|Výsledek|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN>(ne matematickému definovanému čísle)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\<0,8|<xref:System.Double.NegativeInfinity>|  
  
 Při zachycení <xref:System.DivideByZeroException> výjimky můžete použít její členy, které vám pomohou ji zpracovat. Například <xref:System.Exception.Message%2A> vlastnost obsahuje text zprávy pro výjimku. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operace bitového posunutí  
 Operace bitového posunu provádí aritmetické posunutí bitového vzorku. Vzor je obsažen v operandu vlevo, zatímco operand na pravé straně Určuje počet pozic pro posunutí vzorku. Vzor můžete posunout vpravo pomocí [operátoru>> ](../../../language-reference/operators/right-shift-operator.md) nebo vlevo pomocí [operátoru<< ](../../../language-reference/operators/left-shift-operator.md).  
  
 Datový typ operandu vzoru musí být `SByte` ,,, `Byte` , `Short` `UShort` `Integer` , `UInteger` , `Long` nebo `ULong` . Datový typ operandu posunutí hodnoty posunu musí být `Integer` nebo musí být rozšířen na `Integer` .  
  
 Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci. Bitové pozice uvolněné posunutím se nastaví takto:  
  
- 0 pro aritmetický levý posun  
  
- 0 pro aritmetický pravý posun kladného čísla  
  
- 0 pro aritmetický pravý posun typu nepodepsaných dat ( `Byte` , `UShort` , `UInteger` , `ULong` )  
  
- 1 pro aritmetický pravý posun záporného čísla ( `SByte` , `Short` , `Integer` nebo `Long` )  
  
 Následující příklad posune `Integer` hodnotu vlevo a vpravo.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Aritmetické posuny nikdy negenerují výjimky přetečení.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Kromě logických operátorů,, `Not` , `Or` `And` a `Xor` slouží také k provádění bitových aritmetických operací při použití v numerických hodnotách. Další informace naleznete v tématu "bitové operace" v [logických a bitových operátorech v Visual Basic](logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Bezpečnost typů  
 Operandy by měly být obvykle stejného typu. Například pokud se přidáváte k `Integer` proměnné, měli byste ji přidat do jiné `Integer` proměnné a výsledek by měl být také přiřazen proměnné typu `Integer` .  
  
 Jedním ze způsobů, jak zajistit dobrý typ bezpečného kódování, je použití [příkazu Option Strict](../../../language-reference/statements/option-strict-statement.md). Pokud nastavíte `Option Strict On` , Visual Basic automaticky provede převody *bezpečného typu* . Například pokud se pokusíte přidat `Integer` proměnnou do `Double` proměnné a přiřadit hodnotu `Double` proměnné, operace pokračuje normálně, protože `Integer` hodnota může být převedena na `Double` bez ztráty dat. Typ – nebezpečná převod na druhé straně způsobí chybu kompilátoru s `Option Strict On` . Například pokud se pokusíte přidat `Integer` proměnnou do `Double` proměnné a přiřadit hodnotu `Integer` proměnné, výsledek chyby kompilátoru, protože `Double` proměnnou nelze implicitně převést na typ `Integer` .  
  
 Pokud ale nastavíte `Option Strict Off` , Visual Basic umožní provést implicitní zužující převody, i když můžou způsobit neočekávanou ztrátu dat nebo přesnost. Z tohoto důvodu doporučujeme použít `Option Strict On` při psaní kódu v produkčním prostředí. Další informace najdete v tématu [rozšiřování a zúžení převodů](../data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Viz také

- [Aritmetické operátory](../../../language-reference/operators/arithmetic-operators.md)
- [Operátory bitového posunu](../../../language-reference/operators/bit-shift-operators.md)
- [Operátory porovnání v jazyce Visual Basic](comparison-operators.md)
- [Operátory řetězení v jazyce Visual Basic](concatenation-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](logical-and-bitwise-operators.md)
- [Účinná kombinace operátorů](efficient-combination-of-operators.md)
