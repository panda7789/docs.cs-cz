---
title: Ladění stromů výrazů v aplikaci Visual StudioC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 2b858597a01f4d7ce460460956d3efcad856531d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319022"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="ef0b9-102">Ladění stromů výrazů v aplikaci Visual StudioC#()</span><span class="sxs-lookup"><span data-stu-id="ef0b9-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="ef0b9-103">Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="ef0b9-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="ef0b9-104">Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít vlastnost `DebugView`, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="ef0b9-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="ef0b9-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="ef0b9-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Snímek obrazovky nástroj DebugView stromu výrazu v ladicím programu VS](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="ef0b9-107">Vzhledem k tomu, že `DebugView` je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to výběrem možnosti **Vizualizér textu** z ikony lupy vedle popisku `DebugView`.</span><span class="sxs-lookup"><span data-stu-id="ef0b9-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="ef0b9-109">Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:</span><span class="sxs-lookup"><span data-stu-id="ef0b9-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="ef0b9-110">[Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom C# výrazu jako kód:</span><span class="sxs-lookup"><span data-stu-id="ef0b9-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="ef0b9-112">[Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů:</span><span class="sxs-lookup"><span data-stu-id="ef0b9-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Snímek obrazovky Vizualizér stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="ef0b9-114">Otevření Vizualizér pro strom výrazu</span><span class="sxs-lookup"><span data-stu-id="ef0b9-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="ef0b9-115">Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.</span><span class="sxs-lookup"><span data-stu-id="ef0b9-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="ef0b9-116">Zobrazí se seznam dostupných vizualizací.:</span><span class="sxs-lookup"><span data-stu-id="ef0b9-116">A list of available visualizers is displayed.:</span></span> 

    ![Snímek obrazovky znázorňující otevírání vizualizují ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="ef0b9-118">Klikněte na vizualizér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="ef0b9-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef0b9-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ef0b9-119">See also</span></span>

- [<span data-ttu-id="ef0b9-120">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="ef0b9-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="ef0b9-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ef0b9-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="ef0b9-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="ef0b9-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="ef0b9-123">syntaxe `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ef0b9-123">`DebugView` syntax</span></span>](debugview-syntax.md)
