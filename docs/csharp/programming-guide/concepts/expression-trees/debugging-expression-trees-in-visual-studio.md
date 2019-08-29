---
title: Ladění stromů výrazů v aplikaci Visual StudioC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 43091d11dfc1fae3e6f047f35b61e992c5aaf50b
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104911"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Ladění stromů výrazů v aplikaci Visual StudioC#()
Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů. Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte si `DebugView` , že je k dispozici pouze v režimu ladění.)  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Vzhledem `DebugView` k tomu, že je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to tak, že vyberete **Vizualizér textu** z ikony lupy vedle `DebugView` popisku.

 ![U výsledků nástroj DebugView se použije Vizualizér textu](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([Licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), která je k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí C# strom výrazu jako kód:

  ![Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([Licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů:

  ![Vizualizér ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření Vizualizér pro strom výrazu  
  
1. Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.  
  
     Zobrazí se seznam dostupných vizualizací.: 

      ![Otevírání vizualizují ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Klikněte na vizualizér, který chcete použít.  
  
## <a name="see-also"></a>Viz také:

- [Stromy výrazů (C#)](./index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`syntaktick](debugview-syntax.md)
