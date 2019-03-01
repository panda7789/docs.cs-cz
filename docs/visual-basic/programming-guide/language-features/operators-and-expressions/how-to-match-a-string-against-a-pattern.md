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
ms.openlocfilehash: 884c5ddf15deb49719915f10e107ba6a3431c4bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965940"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Postupy: Porovnání řetězce se vzorem (Visual Basic)
Pokud chcete zjistit, zda výraz [datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md) vyhovuje vzoru, můžete použít [operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` má dva operandy. Levý operand je výraz řetězce a pravý operand je řetězec obsahující vzor se použije k porovnání. `Like` Vrátí `Boolean` hodnotu, která udává, zda splňuje řetězcového výrazu vzoru.  
  
 Odpovídá každému znaku v řetězci výraz proti konkrétní znak, zástupných znaků, seznam znak nebo rozsah znaků. Pozice specifikace v řetězci vzoru odpovídají pozic znaků, které mají být obsažena ve řetězcového výrazu.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Odpovídá znaku v řetězcový výraz proti konkrétní znak  
  
-   Umístěte na konkrétní znak přímo řetězec vzoru. Některé speciální znaky musí být uzavřen v závorkách (`[ ]`). Další informace najdete v tématu [operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     Následující příklad testuje, jestli `myString` obsahuje přesně jeden znak `H`.  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Odpovídá znaku v řetězci výraz proti zástupný znak  
  
-   Vložit otazník (`?`) v řetězci vzor. Jakýkoli platný znak na této pozici díky úspěšná shoda.  
  
     Následující příklad testuje, jestli `myString` se skládá z jednoho znaku `W` následovaný přesně dva znaky žádné hodnoty.  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Odpovídá znaku v řetězcového výrazu seznam znaků  
  
-   Umístit závorky (`[ ]`) v řetězci vzor a v závorkách vložit seznam znaků. Pomocí čárky nebo jakéhokoliv jiného oddělovače neoddělujte znaky. Libovolný znak v seznamu je úspěšná shoda.  
  
     Následující příklad testuje, jestli `myString` jakýkoli platný znak následovaný přesně jedním ze znaků se skládá ze `A`, `C`, nebo `E`.  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     Všimněte si, že tuto shodu je velká a malá písmena.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Odpovídá znaku v řetězci výraz proti rozsahu znaků  
  
-   Umístit závorky (`[ ]`) v řetězci vzor a v závorkách do rozsahu znaků nejnižší a nejvyšší oddělené pomlčkou (`–`). Jakémukoli jednomu znaku v rozsahu díky úspěšná shoda.  
  
     Následující příklad testuje, jestli `myString` se skládá ze znaků `num` za nímž následuje přesně jedním ze znaků `i`, `j`, `k`, `l`, `m`, nebo `n`.  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     Všimněte si, že tuto shodu je velká a malá písmena.  
  
## <a name="matching-empty-strings"></a>Odpovídající prázdné řetězce  
 `Like` zpracovává sekvence `[]` jako řetězec nulové délky (`""`). Můžete použít `[]` k ověření, zda výraz celý řetězec je prázdný, ale nemůžete je použít k testování, pokud na konkrétní umístění v řetězcového výrazu je prázdný. Je-li prázdná pozice jednu z možností je potřeba testovat pro, můžete použít `Like` více než jednou.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Odpovídá znaku v řetězci výrazu seznam se znaky ani žádný znak  
  
1.  Volání `Like` operátor dvakrát na stejném řetězcový výraz a dvě volání s buď [nebo operátor](../../../../visual-basic/language-reference/operators/or-operator.md) nebo [OrElse – operátor](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  V řetězci vzor pro první `Like` klauzule, zahrnují seznamu znak uzavřen v závorkách (`[ ]`).  
  
3.  V řetězci vzor pro druhý `Like` klauzule neumisťujte libovolný znak na pozici nejistá.  
  
     Následující příklad testuje sedmičíselné telefonní číslo `phoneNum` přesně tři číslice, za nímž následuje mezeru, pomlčku (`–`), tečku (`.`), nebo žádný znak, následovaný přesně čtyři číslice.  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a>Viz také:
- [Operátory porovnání](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operátory a výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operátor Like](../../../../visual-basic/language-reference/operators/like-operator.md)
- [Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)
