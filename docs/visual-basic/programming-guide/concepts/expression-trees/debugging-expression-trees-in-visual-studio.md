---
title: Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 9aead09e0e9469f13e2d6befbad444d3c7fecabd
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196026"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="52510-102">Ladění stromů výrazů v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52510-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="52510-103">Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="52510-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="52510-104">Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromů výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="52510-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="52510-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="52510-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="52510-107">Protože `DebugView` je řetězec, můžete použít [integrované Vizualizátor textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) zobrazíte na více řádcích, tak, že vyberete **Vizualizátor textu** z ikony lupy vedle `DebugView` Popisek.</span><span class="sxs-lookup"><span data-stu-id="52510-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Vizualizátor textu použitý k výsledkům 'nástroj DebugView.](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="52510-109">Alternativně můžete nainstalovat a používat [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, jako například:</span><span class="sxs-lookup"><span data-stu-id="52510-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

* <span data-ttu-id="52510-110">[Čitelný výrazy](https://github.com/agileobjects/ReadableExpressions) ([licencí MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí stromu výrazů jako C# kódu:</span><span class="sxs-lookup"><span data-stu-id="52510-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Čitelný výrazy vizualizéru](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="52510-112">[Vizualizéru stromu výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencí MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, vlastnosti a související objekty; a může mít za následek stromu výrazů kódu jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="52510-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![ExpressionToString vizualizéru](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="52510-114">Chcete-li otevřít vizualizér pro strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="52510-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="52510-115">Klikněte na ikonu lupy, které se zobrazí vedle stromu výrazů v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna.</span><span class="sxs-lookup"><span data-stu-id="52510-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="52510-116">Zobrazí seznam k dispozici vizualizéry.:</span><span class="sxs-lookup"><span data-stu-id="52510-116">A list of available visualizers is displayed.:</span></span> 

      ![Otevírání vizualizéry ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="52510-118">Klikněte na vizualizaci, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="52510-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="52510-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52510-119">See also</span></span>

- [<span data-ttu-id="52510-120">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52510-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="52510-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="52510-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="52510-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="52510-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="52510-123">`DebugView` Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52510-123">`DebugView` syntax</span></span>](debugview-syntax.md)
