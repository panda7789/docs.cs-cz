---
title: Aritmetické operátory v jazyce Visual Basic
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
ms.openlocfilehash: 635c791f81107a1800e2ef381f6bea78cbc18e18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61830359"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Aritmetické operátory v jazyce Visual Basic
Aritmetické operátory jsou používány k provádění řady známých aritmetické operace, které zahrnují výpočet číselné hodnoty literály, proměnné, ostatní výrazy, funkce a volání vlastností a konstanty. Také klasifikovat s aritmetické operátory jsou bitové posunutí – operátory, které bude fungovat na úrovni jednotlivých bitů operandy a posunout své vzorců bitů doleva nebo doprava.  
  
## <a name="arithmetic-operations"></a>Aritmetické operace  
 Můžete přidat dvě hodnoty ve výrazu spolu s [+ – operátor](../../../../visual-basic/language-reference/operators/addition-operator.md), nebo odstraňte jednu z jiného pomocí [-– operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 Negace také používá [-– operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md), ale s pouze jeden operand, jako následující příklad ukazuje.  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 Použití úlohy násobení a dělení [* – operátor](../../../../visual-basic/language-reference/operators/multiplication-operator.md) a [/ – operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)v uvedeném pořadí, jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 Používá umocnění [^ – operátor](../../../../visual-basic/language-reference/operators/exponentiation-operator.md), jak ukazuje následující příklad.  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 Dělení celého čísla je prováděno [\ – operátor (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md). Celočíselné dělení vrátí podíl, tedy na celé číslo představující počet, kolikrát dělitel lze rozdělit do bez ohledu na jakékoli zbývající podíl. Dělitel a podíl musí být integrální typy (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, a `ULong`) pro tento operátor. Všechny ostatní typy musí být převeden na celočíselný typ nejprve. Následující příklad ukazuje dělení celého čísla.  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 MODULUS aritmetické se provádí pomocí [Mod operátor](../../../../visual-basic/language-reference/operators/mod-operator.md). Tento operátor Vrátí zbytek po dělení dělitel do podíl celočíselný počet časy. Pokud dělitel a Delenec celočíselných typů, vrácená hodnota je integrální. Pokud jsou typy s plovoucí desetinnou čárkou dělení a Delenec, vrácená hodnota je také s plovoucí desetinnou čárkou. Následující příklad ukazuje toto chování.  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>Pokus o dělení nulou  
 Dělení nulou má odlišné výsledky v závislosti na používané datové typy. V integrální divizemi (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyvolá <xref:System.DivideByZeroException> výjimky. V operacích dělení na `Decimal` nebo `Single` datový typ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyvolá také <xref:System.DivideByZeroException> výjimky.  
  
 V plovoucí desetinné čárky divize zahrnující `Double` datový typ, není vyvolána žádná výjimka a výsledkem je člen třídy, představující <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, nebo <xref:System.Double.NegativeInfinity>, v závislosti na podíl. Následující tabulka shrnuje různé výsledky pokusu o dělení `Double` hodnotu nula.  
  
|Delenec datový typ|Dělitel datový typ|Delenec hodnotu|Výsledek|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (není matematicky definované číslo)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 Při zachycení <xref:System.DivideByZeroException> výjimky, můžete pomocí jeho členů můžete ji zpracovat. Například <xref:System.Exception.Message%2A> vlastnost obsahuje text zprávy o výjimce. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="bit-shift-operations"></a>Operace bitového posunutí  
 Bitové posunutí – operace provede aritmetický posun bitový. Vzor je součástí operand na levé straně, zatímco operand na pravé straně určuje počet pozic, chcete-li posunout vzor. Vzor můžete posunout doprava s [>> operátor](../../../../visual-basic/language-reference/operators/right-shift-operator.md) nebo na levé straně s [<< operátor](../../../../visual-basic/language-reference/operators/left-shift-operator.md).  
  
 Datový typ operandu vzor musí být `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`. Datový typ operandu částka shift musí být `Integer` nebo musí rozšířit na `Integer`.  
  
 Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek. Bitové pozice uvolněné pomocí přechodu nastavené takto:  
  
- 0 pro aritmetický operátor posunu vlevo  
  
- 0 pro aritmetické pravého posunutí kladného čísla  
  
- 0 pro aritmetické posunutí doprava bez znaménka datového typu (`Byte`, `UShort`, `UInteger`, `ULong`)  
  
- 1 pro aritmetické pravého posunutí záporné číslo (`SByte`, `Short`, `Integer`, nebo `Long`)  
  
 V následujícím příkladu se posune `Integer` hodnota vlevo a vpravo.  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 Aritmetické staffhubu nikdy generovat výjimky přetečení.  
  
## <a name="bitwise-operations"></a>Bitové operace  
 Kromě toho, že logické operátory `Not`, `Or`, `And`, a `Xor` také provést aritmetický bitový při použití na číselné hodnoty. Další informace najdete v tématu "Bitové operace" v [logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md).  
  
## <a name="type-safety"></a>Bezpečnost typů  
 Obvykle by měl být operandy stejného typu. Například, pokud provádíte přidávání pomocí `Integer` proměnných, měli byste přidat ho do jiného `Integer` proměnné kde by měl výsledek přiřaďte proměnné typu `Integer` také.  
  
 Jeden ze způsobů, jak zajistit správné typově bezpečný postup kódování je použít [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md). Pokud nastavíte `Option Strict On`, Visual Basic automaticky provede *zajišťující bezpečnost typů* převody. Například, pokud se pokusíte přidat `Integer` proměnné `Double` proměnnou a přiřaďte hodnotu k `Double` proměnné, operace pokračuje obvykle, protože `Integer` hodnotu lze převést na `Double` bez ztráty dat. Typ nebezpečné převody, na druhé straně způsobí chybu kompilátoru s `Option Strict On`. Například, pokud se pokusíte přidat `Integer` proměnné `Double` proměnnou a přiřaďte hodnotu k `Integer` proměnné, k chybě kompilátoru dojde, protože `Double` proměnnou nelze implicitně převést na typ `Integer`.  
  
 Pokud nastavíte `Option Strict Off`, ale jazyka Visual Basic umožňuje implicitní zužující převody uskutečnit, i když může způsobit neočekávané ztráty dat nebo přesnosti. Z tohoto důvodu doporučujeme používat `Option Strict On` při psaní kódu produkčního prostředí. Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
## <a name="see-also"></a>Viz také:

- [Aritmetické operátory](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory bitového posunu](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory řetězení v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Logické a bitové operátory v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
