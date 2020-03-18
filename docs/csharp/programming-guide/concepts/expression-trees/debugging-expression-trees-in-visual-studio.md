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
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="18967-102">Ladění stromů výrazů v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="18967-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="18967-103">Můžete analyzovat strukturu a obsah stromů výrazů při ladění aplikací.</span><span class="sxs-lookup"><span data-stu-id="18967-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="18967-104">Chcete-li získat rychlý přehled o stromové `DebugView` struktuře výrazů, můžete použít vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="18967-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="18967-105">(Všimněte `DebugView` si, že je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="18967-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Snímek obrazovky s ladicím zobrazením stromu výrazů v ladicím programu VS](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="18967-107">Vzhledem k `DebugView` tomu, že je řetězec, můžete použít vestavěný [vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) k jeho zobrazení na více řádcích výběrem **vizualizéru textu** z ikony lupy vedle popisku. `DebugView`</span><span class="sxs-lookup"><span data-stu-id="18967-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Snímek obrazovky s vizualizérem textu použitým na výsledky zobrazení Ladění](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="18967-109">Alternativně můžete nainstalovat a použít [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:</span><span class="sxs-lookup"><span data-stu-id="18967-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="18967-110">[Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) [(licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostupné na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako kód jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="18967-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Snímek obrazovky vizualizéru Čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="18967-112">[Vizualizér výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů:</span><span class="sxs-lookup"><span data-stu-id="18967-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Snímek obrazovky vizualizéru stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="18967-114">Otevření vizualizéru pro strom výrazů</span><span class="sxs-lookup"><span data-stu-id="18967-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="18967-115">Klepněte na ikonu **lupy,** která se zobrazí vedle stromu výrazů v **okně DataTips**, v okně **Kukátka,** v okně Autos nebo v okně **Locals.**</span><span class="sxs-lookup"><span data-stu-id="18967-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="18967-116">Zobrazí se seznam dostupných vizualizérů:</span><span class="sxs-lookup"><span data-stu-id="18967-116">A list of available visualizers is displayed.:</span></span>

    ![Snímek obrazovky s otevřením vizualizérů z Visual Studia](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="18967-118">Klikněte na vizualizér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="18967-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18967-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="18967-119">See also</span></span>

- [<span data-ttu-id="18967-120">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="18967-120">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="18967-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="18967-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="18967-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="18967-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="18967-123">`DebugView`Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18967-123">`DebugView` syntax</span></span>](debugview-syntax.md)
