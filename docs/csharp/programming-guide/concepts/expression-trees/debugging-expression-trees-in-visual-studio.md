---
title: Ladění stromů výrazů v aplikaci Visual StudioC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 30f538712881e41b4fd0e62d06f74373d755ea40
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195682"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v aplikaci Visual StudioC#()
Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů. Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít vlastnost `DebugView`, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)  

![Snímek obrazovky nástroj DebugView stromu výrazu v ladicím programu VS](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

Vzhledem k tomu, že `DebugView` je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to výběrem možnosti **Vizualizér textu** z ikony lupy vedle popisku `DebugView`.

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom C# výrazu jako kód:

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů:

  ![Snímek obrazovky Vizualizér stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření Vizualizér pro strom výrazu  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.  

    Zobrazí se seznam dostupných vizualizací.: 

    ![Snímek obrazovky znázorňující otevírání vizualizují ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Klikněte na vizualizér, který chcete použít.  
  
## <a name="see-also"></a>Viz také:

- [Stromy výrazů (C#)](./index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [syntaxe `DebugView`](debugview-syntax.md)
