---
title: Ladění stromů výrazů v sadě Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 2c4b1fec389a8ee168b890339ce11af596581cbc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378800"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Ladění stromů výrazů v aplikaci Visual Studio (Visual Basic)
Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů. Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)  

![Snímek obrazovky nástroj DebugView stromu výrazu](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Vzhledem k `DebugView` tomu, že je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to tak, že vyberete **Vizualizér textu** z ikony lupy vedle `DebugView` popisku.

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako motivový kód C# s různými možnostmi vykreslování:

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů. a lze strom výrazu vykreslit pomocí Visual Basicho kódu:

  ![Snímek obrazovky Vizualizér ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření Vizualizér pro strom výrazu  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.  
  
    Zobrazí se seznam dostupných vizualizací.:

    ![Snímek obrazovky uživatele otevírající vizualizace ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Klikněte na vizualizér, který chcete použít.  

## <a name="see-also"></a>Viz také

- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`syntaktick](debugview-syntax.md)
