---
title: Ladění stromů výrazů v aplikaci Visual Studio (C#)
description: Přečtěte si o vlastnosti nástroj DebugView v aplikaci Visual Studio. Podívejte se, jak tuto vlastnost použít k analýze struktury a obsahu stromů výrazů.
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 5d62a5e6fa5ce537a1ea8b316e7322eb976200c0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105639"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="f61e5-104">Ladění stromů výrazů v aplikaci Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="f61e5-104">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="f61e5-105">Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="f61e5-105">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="f61e5-106">Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="f61e5-106">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="f61e5-107">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="f61e5-107">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Snímek obrazovky nástroj DebugView stromu výrazu v ladicím programu VS](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

<span data-ttu-id="f61e5-109">Vzhledem k `DebugView` tomu, že je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to tak, že vyberete **Vizualizér textu** z ikony lupy vedle `DebugView` popisku.</span><span class="sxs-lookup"><span data-stu-id="f61e5-109">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

<span data-ttu-id="f61e5-111">Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:</span><span class="sxs-lookup"><span data-stu-id="f61e5-111">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="f61e5-112">[Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako motivový kód C# s různými možnostmi vykreslování:</span><span class="sxs-lookup"><span data-stu-id="f61e5-112">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="f61e5-114">[Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licence MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) poskytuje stromové zobrazení stromu výrazu a jeho jednotlivých uzlů:</span><span class="sxs-lookup"><span data-stu-id="f61e5-114">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes:</span></span>

  ![Snímek obrazovky Vizualizér stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="f61e5-116">Otevření Vizualizér pro strom výrazu</span><span class="sxs-lookup"><span data-stu-id="f61e5-116">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="f61e5-117">Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.</span><span class="sxs-lookup"><span data-stu-id="f61e5-117">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  

    <span data-ttu-id="f61e5-118">Zobrazí se seznam dostupných vizualizací.:</span><span class="sxs-lookup"><span data-stu-id="f61e5-118">A list of available visualizers is displayed.:</span></span>

    ![Snímek obrazovky znázorňující otevírání vizualizují ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. <span data-ttu-id="f61e5-120">Klikněte na vizualizér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="f61e5-120">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f61e5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f61e5-121">See also</span></span>

- [<span data-ttu-id="f61e5-122">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="f61e5-122">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="f61e5-123">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f61e5-123">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="f61e5-124">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="f61e5-124">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="f61e5-125">`DebugView`syntaktick</span><span class="sxs-lookup"><span data-stu-id="f61e5-125">`DebugView` syntax</span></span>](debugview-syntax.md)
