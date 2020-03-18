---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: cf1708d1155e48d8609baca2067baa66dae08c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169685"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v sadě Visual Studio (C#)
Můžete analyzovat strukturu a obsah stromů výrazů při ladění aplikací. Chcete-li získat rychlý přehled o stromové `DebugView` struktuře výrazů, můžete použít vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte `DebugView` si, že je k dispozici pouze v režimu ladění.)  

![Snímek obrazovky s ladicím zobrazením stromu výrazů v ladicím programu VS](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

Vzhledem k `DebugView` tomu, že je řetězec, můžete použít vestavěný [vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) k jeho zobrazení na více řádcích výběrem **vizualizéru textu** z ikony lupy vedle popisku. `DebugView`

 ![Snímek obrazovky s vizualizérem textu použitým na výsledky zobrazení Ladění](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Alternativně můžete nainstalovat a použít [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) [(licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostupné na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako kód jazyka C#:

  ![Snímek obrazovky vizualizéru Čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Vizualizér výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů:

  ![Snímek obrazovky vizualizéru stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření vizualizéru pro strom výrazů  
  
1. Klepněte na ikonu **lupy,** která se zobrazí vedle stromu výrazů v **okně DataTips**, v okně **Kukátka,** v okně Autos nebo v okně **Locals.**  

    Zobrazí se seznam dostupných vizualizérů:

    ![Snímek obrazovky s otevřením vizualizérů z Visual Studia](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Klikněte na vizualizér, který chcete použít.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](./index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`Syntaxe](debugview-syntax.md)
