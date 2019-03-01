---
title: 'Postupy: Výpočet numerických hodnot (Visual Basic)'
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
ms.openlocfilehash: 036985a7b60afedc1e8ef0854c619ea8515e5ffe
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974299"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Postupy: Výpočet numerických hodnot (Visual Basic)
Můžete vypočítat číselných hodnot pomocí numerických výrazů. A *číselného výrazu* je výraz, který obsahuje literály a konstanty a proměnné představující číselné hodnoty a operátory, které fungují u těchto hodnot.  
  
## <a name="calculating-numeric-values"></a>Probíhá výpočet číselné hodnoty  
  
#### <a name="to-calculate-a-numeric-value"></a>Pro výpočet číselné hodnoty  
  
-   Zkombinujte jeden nebo více číselné literály, konstanty a proměnné do číselného výrazu. Následující příklad ukazuje některé platné numerických výrazů.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     První tři řádky zobrazují literál, konstanty a proměnné. Každé z nich tvoří platný číselný výraz samotný. Poslední řádek ukazuje kombinaci proměnné se dva literály.  
  
     Všimněte si, že číselného výrazu netvoří úplný příkaz jazyka Visual Basic samostatně. Výraz musí používat jako součást dokončení příkazu.  
  
#### <a name="to-store-a-numeric-value"></a>K uložení číselné hodnoty  
  
-   Přiřazovací příkaz můžete použít k přiřazení hodnoty reprezentována číselné proměnné, jak ukazuje následující příklad.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     V předchozím příkladu, hodnota výrazu na pravé straně operátor je rovno (`=`) je přiřazená k proměnné `j` na levé straně operátoru, takže `j` vyhodnocen jako 276.  
  
     Další informace najdete v tématu [příkazy](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Více operátorů  
 Pokud číselný výraz obsahuje více než jeden operátor, pořadí, ve kterém jsou vyhodnoceny je určen podle pravidel priority operátorů. K přepsání pravidel priority operátorů, uzavřete výrazy v závorkách, stejně jako v předchozím příkladu; uzavřené výrazy jsou nejdříve vyhodnocovány.  
  
#### <a name="to-override-normal-operator-precedence"></a>Chcete-li přepsat operátor normální priorita  
  
-   Použití závorek k uzavření operace, které chcete provést jako první. Následující příklad ukazuje dva různé výsledky se stejnými operandy a operátory.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     V předchozím příkladu, pro výpočet `j` provede operátor sčítání (`+`) první protože závorky kolem `(67 + i)` přepsání normální priorita a hodnota přiřazená k `j` je 276 (4 x 69). Výpočet pro `k` provádí operátory v jejich normální priorita (`*` před `+`) a hodnota přiřazená k `k` je 270 (268 plus 2).  
  
     Další informace najdete v tématu [priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Viz také:
- [Operátory a výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Příkazy](../../../../visual-basic/language-reference/statements/index.md)
- [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Aritmetické operátory](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
