---
title: 'Postupy: Porovnání řetězce se vzorem'
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
ms.openlocfilehash: d8a3c363d1a443db4a0b7633e380562af1913aca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403443"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Postupy: Porovnání řetězce se vzorem (Visual Basic)

Pokud chcete zjistit, zda výraz [řetězcového datového typu](../../../language-reference/data-types/string-data-type.md) splňuje vzor, lze použít [operátor LIKE](../../../language-reference/operators/like-operator.md).

`Like`přebírá dva operandy. Levý operand je řetězcový výraz a pravý operand je řetězec obsahující vzor, který se má použít pro porovnávání. `Like`Vrátí `Boolean` hodnotu, která označuje, zda řetězcový výraz vyhovuje vzoru.

Každý znak v řetězcovém výrazu můžete porovnat s konkrétním znakem, zástupným znakem, seznamem znaků nebo rozsahem znaků. Pozice specifikací v řetězci vzoru odpovídají polohám znaků, které mají být ve výrazu řetězce spárovány.

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Chcete-li porovnat znak v řetězcovém výrazu proti určitému znaku

Konkrétní znak umístěte přímo do řetězce vzoru. Některé speciální znaky musí být uzavřeny do závorek ( `[ ]` ). Další informace naleznete v tématu [operátor LIKE](../../../language-reference/operators/like-operator.md).

Následující příklad testuje, zda `myString` je tvořen přesně jedním znakem `H` .

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Chcete-li porovnat znak ve výrazu řetězce se zástupným znakem

Vložte otazník ( `?` ) do řetězce vzoru. Libovolný platný znak v této pozici provede úspěšnou shodu.

Následující příklad testuje, zda `myString` se skládá z jednoho znaku `W` následovanýho přesně dvěma znaky libovolné hodnoty.

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Chcete-li porovnat znak ve výrazu řetězce se seznamem znaků

Vložte hranaté závorky ( `[ ]` ) do řetězce vzorů a uvnitř závorek vložte seznam znaků. Znaky nedělte čárkami ani žádné jiné oddělovače. Libovolný jeden znak v seznamu provede úspěšnou shodu.

Následující příklad testuje, zda `myString` obsahuje libovolný platný znak následovaný přesně jedním ze znaků `A` , `C` nebo `E` .

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

Všimněte si, že tato shoda rozlišuje velká a malá písmena.

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Chcete-li porovnat znak ve výrazu řetězce s rozsahem znaků

Vložte hranaté závorky ( `[ ]` ) do řetězce vzorů a uvnitř závorek vložte nejnižší a nejvyšší znaky v rozsahu oddělené spojovníkem ( `–` ). Libovolný jednotlivý znak v rozsahu provede úspěšnou shodu.

Následující příklad testuje, zda `myString` se skládá ze znaků `num` následovaných právě jedním ze znaků `i` ,,,, `j` `k` `l` `m` nebo `n` .

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

Všimněte si, že tato shoda rozlišuje velká a malá písmena.

## <a name="matching-empty-strings"></a>Porovnání prázdných řetězců

`Like`zpracuje sekvenci `[]` jako řetězec s nulovou délkou ( `""` ). Můžete použít `[]` k otestování, zda je celý řetězcový výraz prázdný, ale nelze jej použít k otestování, pokud je určitá pozice ve výrazu řetězce prázdná. Pokud je prázdná pozice jednou z možností, které je třeba otestovat, můžete použít `Like` více než jednou.

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Chcete-li porovnat znak ve výrazu řetězce se seznamem znaků nebo žádným znakem

1. Zavolejte `Like` operátor dvakrát u stejného řetězcového výrazu a připojte dvě volání pomocí [operátoru OR](../../../language-reference/operators/or-operator.md) nebo [operátoru OrElse](../../../language-reference/operators/orelse-operator.md).

2. V řetězci vzoru pro první `Like` klauzuli uveďte seznam znaků uzavřený do závorek ( `[ ]` ).

3. V řetězci vzoru pro druhou `Like` klauzuli neumísťujte žádný znak na pozici v daném umístění.

    Následující příklad testuje sedm číslic telefonního čísla `phoneNum` pro přesně tři číselné číslice, za kterými následuje mezera, spojovník ( `–` ), tečka ( `.` ) nebo žádný znak, následovaný přesně čtyřmi číselnými číslicemi.

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>Viz také

- [Operátory porovnání](../../../language-reference/operators/comparison-operators.md)
- [Operátory a výrazy](index.md)
- [Like – operátor](../../../language-reference/operators/like-operator.md)
- [Datový typ String](../../../language-reference/data-types/string-data-type.md)
