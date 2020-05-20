---
title: Ladění stromů výrazů v sadě Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 287f3096a1af8b9fa42d252c5240d7caefa6bac8
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616892"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="3c1bd-102">Ladění stromů výrazů v aplikaci Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c1bd-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="3c1bd-103">Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="3c1bd-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="3c1bd-104">Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="3c1bd-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="3c1bd-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="3c1bd-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Snímek obrazovky nástroj DebugView stromu výrazu](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="3c1bd-107">Vzhledem k `DebugView` tomu, že je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to tak, že vyberete **Vizualizér textu** z ikony lupy vedle `DebugView` popisku.</span><span class="sxs-lookup"><span data-stu-id="3c1bd-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="3c1bd-109">Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:</span><span class="sxs-lookup"><span data-stu-id="3c1bd-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="3c1bd-110">[Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako motivový kód C# s různými možnostmi vykreslování:</span><span class="sxs-lookup"><span data-stu-id="3c1bd-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as themeable C# code, with various rendering options:</span></span>

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="3c1bd-112">[Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([licence MIT](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) poskytuje stromové zobrazení stromu výrazu a jeho jednotlivých uzlů. a lze strom výrazu vykreslit pomocí Visual Basic syntaxe:</span><span class="sxs-lookup"><span data-stu-id="3c1bd-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/README.md) ([MIT license](https://github.com/zspitz/ExpressionTreeVisualizer/blob/master/LICENSE)) provides a tree view of the expression tree and its individual nodes; and can render the expression tree using Visual Basic syntax:</span></span>

  ![Snímek obrazovky Vizualizér stromu výrazů](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="3c1bd-114">Otevření Vizualizér pro strom výrazu</span><span class="sxs-lookup"><span data-stu-id="3c1bd-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="3c1bd-115">Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.</span><span class="sxs-lookup"><span data-stu-id="3c1bd-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="3c1bd-116">Zobrazí se seznam dostupných vizualizací.:</span><span class="sxs-lookup"><span data-stu-id="3c1bd-116">A list of available visualizers is displayed.:</span></span>

    ![Snímek obrazovky uživatele otevírající vizualizace ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="3c1bd-118">Klikněte na vizualizér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="3c1bd-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3c1bd-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c1bd-119">See also</span></span>

- [<span data-ttu-id="3c1bd-120">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c1bd-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="3c1bd-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3c1bd-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="3c1bd-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="3c1bd-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="3c1bd-123">`DebugView`syntaktick</span><span class="sxs-lookup"><span data-stu-id="3c1bd-123">`DebugView` syntax</span></span>](debugview-syntax.md)
