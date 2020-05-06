---
title: Ladění stromů výrazů v aplikaci Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 6fd9580df64929f553eca29a72f06c5fce2ca878
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796080"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v aplikaci Visual Studio (C#)
Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů. Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte si `DebugView` , že je k dispozici pouze v režimu ladění.)  

![Snímek obrazovky nástroj DebugView stromu výrazu v ladicím programu VS](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

Vzhledem `DebugView` k tomu, že je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to tak, že vyberete **Vizualizér textu** z ikony lupy vedle `DebugView` popisku.

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako motivový kód C# s různými možnostmi vykreslování:

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů:

  ![Snímek obrazovky Vizualizér stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření Vizualizér pro strom výrazu  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.  

    Zobrazí se seznam dostupných vizualizací.:

    ![Snímek obrazovky znázorňující otevírání vizualizují ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Klikněte na vizualizér, který chcete použít.  
  
## <a name="see-also"></a>Viz také

- [Stromy výrazů (C#)](./index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`syntaktick](debugview-syntax.md)
