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
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="15481-102">Ladění stromů výrazů v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15481-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="15481-103">Můžete analyzovat strukturu a obsah stromů výrazů při ladění aplikací.</span><span class="sxs-lookup"><span data-stu-id="15481-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="15481-104">Chcete-li získat rychlý přehled o stromové `DebugView` struktuře výrazů, můžete použít vlastnost, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="15481-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="15481-105">(Všimněte `DebugView` si, že je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="15481-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Snímek obrazovky stromu ladicích zobrazení výrazů](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="15481-107">Vzhledem k `DebugView` tomu, že je řetězec, můžete použít vestavěný [vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) k jeho zobrazení na více řádcích výběrem **vizualizéru textu** z ikony lupy vedle popisku. `DebugView`</span><span class="sxs-lookup"><span data-stu-id="15481-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Snímek obrazovky vizualizéru textu aplikovaný na výsledky zobrazení Ladění](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="15481-109">Alternativně můžete nainstalovat a použít [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:</span><span class="sxs-lookup"><span data-stu-id="15481-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="15481-110">[Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) [(licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostupné na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom výrazů jako kód jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="15481-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Snímek obrazovky vizualizéru Čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="15481-112">[Vizualizér výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů; a může vykreslit strom výrazů pomocí kódu jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="15481-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![Snímek obrazovky vizualizéru ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="15481-114">Otevření vizualizéru pro strom výrazů</span><span class="sxs-lookup"><span data-stu-id="15481-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="15481-115">Klepněte na ikonu **lupy,** která se zobrazí vedle stromu výrazů v **okně DataTips**, v okně **Kukátka,** v okně Autos nebo v okně **Locals.**</span><span class="sxs-lookup"><span data-stu-id="15481-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="15481-116">Zobrazí se seznam dostupných vizualizérů:</span><span class="sxs-lookup"><span data-stu-id="15481-116">A list of available visualizers is displayed.:</span></span>

    ![Snímek obrazovky s uživatelem otevírajícími vizualizéry z Visual Studia](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="15481-118">Klikněte na vizualizér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="15481-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="15481-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="15481-119">See also</span></span>

- [<span data-ttu-id="15481-120">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="15481-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="15481-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="15481-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="15481-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="15481-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="15481-123">`DebugView`Syntaxe</span><span class="sxs-lookup"><span data-stu-id="15481-123">`DebugView` syntax</span></span>](debugview-syntax.md)
