---
title: Ladění stromů výrazů v sadě Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: c6c44d079ab0854b2325b82d3569280752da32fb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266830"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
Můžete analyzovat strukturu a obsah stromů výrazů při ladění aplikací. Chcete-li získat rychlý přehled o stromové `DebugView` struktuře výrazů, můžete použít vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md). (Všimněte `DebugView` si, že je k dispozici pouze v režimu ladění.)  

![Snímek obrazovky stromu ladicích zobrazení výrazů](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Vzhledem k `DebugView` tomu, že je řetězec, můžete použít vestavěný [vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) k jeho zobrazení na více řádcích výběrem **vizualizéru textu** z ikony lupy vedle popisku. `DebugView`

 ![Snímek obrazovky vizualizéru textu aplikovaný na výsledky zobrazení Ladění](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternativně můžete nainstalovat a použít [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:

- [Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) [(licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostupné na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako kód jazyka C#:

  ![Snímek obrazovky vizualizéru Čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Vizualizér výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů; a může vykreslit strom výrazů pomocí kódu jazyka Visual Basic:

  ![Snímek obrazovky vizualizéru ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Otevření vizualizéru pro strom výrazů  
  
1. Klepněte na ikonu **lupy,** která se zobrazí vedle stromu výrazů v **okně DataTips**, v okně **Kukátka,** v okně Autos nebo v okně **Locals.**  
  
    Zobrazí se seznam dostupných vizualizérů:

    ![Snímek obrazovky s uživatelem otevírajícími vizualizéry z Visual Studia](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Klikněte na vizualizér, který chcete použít.  

## <a name="see-also"></a>Viz také

- [Stromy výrazů (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Ladění v sadě Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Vytváření vlastních vizualizérů](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`Syntaxe](debugview-syntax.md)
