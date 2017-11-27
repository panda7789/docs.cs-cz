---
title: "Postupy: Výpočet numerických hodnot (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Postupy: Výpočet numerických hodnot (Visual Basic)
Můžete vypočítat číselné hodnoty prostřednictvím numerických výrazů. A *číselného výrazu* je výraz, který obsahuje literály, konstanty a proměnné představující číselné hodnoty a operátory, které fungují v těchto hodnot.  
  
## <a name="calculating-numeric-values"></a>Výpočet numerických hodnot  
  
#### <a name="to-calculate-a-numeric-value"></a>Chcete-li vypočítat číselná hodnota  
  
-   Jeden nebo více číselné literály, konstanty a proměnné Kombinujte do číselného výrazu. Následující příklad ukazuje některé platné numerických výrazů.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     První tři řádky zobrazit literál, konstanty a proměnné. Každé z nich tvoří platný číselného výrazu samostatně. Poslední řádek zobrazuje kombinaci proměnná s dvěma literály.  
  
     Všimněte si, že číselného výrazu netvoří úplná [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] příkaz samostatně. Výraz musí používat jako součást dokončení příkazu.  
  
#### <a name="to-store-a-numeric-value"></a>K uložení číselná hodnota  
  
-   Příkazu přiřazení můžete přiřadit hodnotu reprezentována číselného výrazu proměnné, jak ukazuje následující příklad.  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     V předchozím příkladu, hodnota výrazu na pravé straně operátor je rovno (`=`) je přiřazen k proměnné `j` na levé straně operátoru, takže `j` se vyhodnocuje 276.  
  
     Další informace najdete v tématu [příkazy](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Několik operátorů  
 Pokud číselný výraz obsahuje více než jeden operátor, pořadí, ve kterém jsou vyhodnocovány je určen podle pravidel objektů operátorů. Chcete-li přepsat pravidla operátorů, uzavřete výrazy v závorkách, jako v předchozím příkladu; výrazy závorkách se vyhodnocují jako první.  
  
#### <a name="to-override-normal-operator-precedence"></a>Chcete-li přepsat normální priorita operátorů  
  
-   Závorky lze použijte k uzavřete operace, které chcete provést první. Následující příklad ukazuje dva odlišné výsledky se stejným operandy a operátory.  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     V předchozím příkladu, výpočtu pro `j` provede operátor sčítání (`+`) první protože závorky `(67 + i)` přepsání normální prioritu a hodnotu přiřazenou `j` je 276 (4 časy 69). Výpočet pro `k` provede operátory v jejich normálním prioritu (`*` před `+`) a hodnotu přiřazenou `k` je 270 (268 plus 2).  
  
     Další informace najdete v tématu [operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Viz také  
 [Operátory a výrazy](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Porovnání hodnot](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Příkazy](../../../../visual-basic/language-reference/statements/index.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Aritmetické operátory](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Účinná kombinace operátorů](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
