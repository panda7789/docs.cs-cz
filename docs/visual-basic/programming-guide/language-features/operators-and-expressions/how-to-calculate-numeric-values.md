---
title: 'Postupy: Výpočet numerických hodnot'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 94b02693f308dcfcfa6983f2750a26d9d419f7be
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403456"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Postupy: Výpočet numerických hodnot (Visual Basic)
Číselné hodnoty můžete vypočítat pomocí numerických výrazů. *Číselný výraz* je výraz, který obsahuje literály, konstanty a proměnné představující číselné hodnoty a operátory, které na těchto hodnotách působí.  
  
## <a name="calculating-numeric-values"></a>Výpočet číselných hodnot  
  
#### <a name="to-calculate-a-numeric-value"></a>Výpočet číselné hodnoty  
  
- Kombinace jednoho nebo více číselných literálů, konstant a proměnných do číselného výrazu. Následující příklad ukazuje některé platné číselné výrazy.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     První tři řádky ukazují literál, konstantu a proměnnou. Každá z nich má platný numerický výraz sám o sobě. Poslední řádek ukazuje kombinaci proměnné se dvěma literály.  
  
     Všimněte si, že číselný výraz netvoří úplný příkaz Visual Basic sám sebou. Výraz je nutné použít jako součást příkazu Complete.  
  
#### <a name="to-store-a-numeric-value"></a>Uložení číselné hodnoty  
  
- Můžete použít příkaz přiřazení pro přiřazení hodnoty reprezentované číselným výrazem proměnné, jak ukazuje následující příklad.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     V předchozím příkladu je hodnota výrazu na pravé straně operátoru rovnosti ( `=` ) přiřazena proměnné `j` na levé straně operátoru, takže se `j` vyhodnotí jako 276.  
  
     Další informace najdete v tématu [příkazy](../../../language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Více operátorů  
 Pokud číselný výraz obsahuje více než jeden operátor, pořadí, ve kterém jsou vyhodnocovány, je určeno pravidly priority operátoru. Chcete-li přepsat pravidla přednosti operátorů, můžete uzavřít výrazy v závorkách, jako v předchozím příkladu. vložené výrazy jsou vyhodnoceny jako první.  
  
#### <a name="to-override-normal-operator-precedence"></a>Přepsání priority normálního operátoru  
  
- K uzavření operací, které chcete provést jako první, použijte kulaté závorky. Následující příklad ukazuje dva různé výsledky se stejnými operandy a operátory.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     V předchozím příkladu výpočet pro `j` provede operátor sčítání ( `+` ) nejprve, protože kulaté závorky kolem `(67 + i)` normální priority přepisují a hodnota přiřazená `j` je 276 (4 časy 69). Výpočet pro `k` provede operátory v normální přednosti ( `*` před `+` ) a hodnota přiřazená `k` je 270 (268 plus 2).  
  
     Další informace najdete v tématu [Priorita operátorů v Visual Basic](../../../language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Viz také

- [Operátory a výrazy](index.md)
- [Porovnání hodnot](value-comparisons.md)
- [Příkazy](../../../language-reference/statements/index.md)
- [Priorita operátorů v jazyce Visual Basic](../../../language-reference/operators/operator-precedence.md)
- [Aritmetické operátory](../../../language-reference/operators/arithmetic-operators.md)
- [Účinná kombinace operátorů](efficient-combination-of-operators.md)
