---
title: 'Postupy: Porovnání řetězce se vzorem (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: aef378bfc32d6deff431a2caac1261a6cd7520c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655209"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Postupy: Porovnání řetězce se vzorem (Visual Basic)
Pokud chcete zjistit, zda výraz, který [String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md) splňuje vzor, pak můžete použít [jako operátor](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` má dva operandy. Levý operand je řetězcového výrazu a pravý operand řetězec obsahující vzor, který se má použít k porovnání. `Like` Vrátí `Boolean` hodnotu, která určuje, zda splňuje řetězcového výrazu vzoru.  
  
 Je možné porovnávat každý znak v řetězcového výrazu proti konkrétní znak, zástupný znak, seznamu znaků nebo rozsah znaků. Pozice specifikace v řetězci vzor odpovídají pozice znaků, které mají být obsažena ve řetězcového výrazu.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Tak, aby odpovídaly znak v řetězcového výrazu proti konkrétní znak  
  
-   Uveďte daného znaku přímo v řetězec. Některé speciální znaky musí být uzavřena do hranatých závorek (`[ ]`). Další informace najdete v tématu [jako operátor](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     Následující příklad testy zda `myString` se skládá právě z jednoho znaku `H`.  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Tak, aby odpovídaly znak v řetězcového výrazu proti zástupný znak  
  
-   Uveďte otazník (`?`) v řetězci vzor. Libovolný platný znak v této pozici Díky úspěšné shody.  
  
     Následující příklad testy zda `myString` se skládá z jednoho znaku `W` následované přesně dva znaky žádné hodnoty.  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Tak, aby odpovídaly znak v řetězcového výrazu podle seznamu znaků  
  
-   Uveďte závorky (`[ ]`) v řetězci vzor a v závorkách put seznamu znaků. Není jednotlivé znaky oddělte čárkami nebo jiný oddělovač. Libovolný znak v seznamu Díky úspěšné shody.  
  
     Následující příklad testy zda `myString` se skládá z libovolný platný znak právě jeden z znaky následované `A`, `C`, nebo `E`.  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Upozorňujeme, že toto porovnání se malá a velká písmena.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Tak, aby odpovídaly znak v řetězcového výrazu proti rozsah znaků  
  
-   Uveďte závorky (`[ ]`) v řetězci vzor a v závorkách put nejnižší a nejvyšší znaky v rozsahu, oddělené pomlčkou (`–`). Libovolný znak v rozsahu Díky úspěšné shody.  
  
     Následující příklad testy zda `myString` tvořený znaky `num` právě jeden z znaky následované `i`, `j`, `k`, `l`, `m`, nebo `n`.  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Upozorňujeme, že toto porovnání se malá a velká písmena.  
  
## <a name="matching-empty-strings"></a>Odpovídající prázdné řetězce  
 `Like` zpracovává sekvenci `[]` jako řetězec nulové délky (`""`). Můžete použít `[]` k ověření, zda je výraz celý řetězec prázdný, ale nemůžete ji použít k testování, pokud na konkrétní pozici v řetězcového výrazu je prázdný. Je-li prázdné pozice jednu z možností je potřeba provést testování pro můžete použít `Like` více než jednou.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Tak, aby odpovídaly znak ve výrazu řetězec seznam znaky ani žádný znak  
  
1.  Volání `Like` operátor dvakrát ve stejném řetězcový výraz a připojení dvě volání s buď [operátor nebo](../../../../visual-basic/language-reference/operators/or-operator.md) nebo [orelse – operátor](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  V řetězci vzor pro první `Like` klauzule, zahrnují seznamu znaků v závorkách (`[ ]`).  
  
3.  V řetězci vzor pro druhý `Like` klauzuli nevkládejte libovolný znak na pozici nejistá.  
  
     Následující příklad testy 7 číslic telefonního čísla `phoneNum` přesně tři číslice, za nímž následuje mezery, pomlčky (`–`), tečku (`.`), nebo žádný znak vůbec, následované přesně čtyři číslice.  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Operátory a výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
