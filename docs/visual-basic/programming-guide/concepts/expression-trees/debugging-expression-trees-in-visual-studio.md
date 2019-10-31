---
title: Ladění stromů výrazů v aplikaci Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: b27ab41f3c3d9bd488fd0f7aaa5010f2997946de
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198268"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Ladění stromů výrazů v aplikaci Visual Studio (Visual Basic)
Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů. Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít vlastnost `DebugView`, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)  

![Snímek obrazovky nástroj DebugView stromu výrazu](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Vzhledem k tomu, že `DebugView` je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to výběrem možnosti **Vizualizér textu** z ikony lupy vedle popisku `DebugView`.

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom C# výrazu jako kód:

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů. a lze strom výrazu vykreslit pomocí Visual Basicho kódu:

  ![Snímek obrazovky Vizualizér ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření Vizualizér pro strom výrazu  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.  
  
    Zobrazí se seznam dostupných vizualizací.: 

    ![Snímek obrazovky uživatele otevírající vizualizace ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Klikněte na vizualizér, který chcete použít.  

## <a name="see-also"></a>Viz také:

- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [syntaxe `DebugView`](debugview-syntax.md)
