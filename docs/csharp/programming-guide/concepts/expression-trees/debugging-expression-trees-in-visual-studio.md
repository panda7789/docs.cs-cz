---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 93b1b660181cd81c31055f5d30d43e535171bb55
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195989"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="bd74b-102">Ladění stromů výrazů v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="bd74b-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="bd74b-103">Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="bd74b-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="bd74b-104">Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromů výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="bd74b-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="bd74b-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="bd74b-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="bd74b-107">Protože `DebugView` je řetězec, můžete použít [integrované Vizualizátor textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) zobrazíte na více řádcích, tak, že vyberete **Vizualizátor textu** z ikony lupy vedle `DebugView` Popisek.</span><span class="sxs-lookup"><span data-stu-id="bd74b-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Vizualizátor textu použitý k výsledkům 'nástroj DebugView.](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="bd74b-109">Alternativně můžete nainstalovat a používat [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, jako například:</span><span class="sxs-lookup"><span data-stu-id="bd74b-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

* <span data-ttu-id="bd74b-110">[Čitelný výrazy](https://github.com/agileobjects/ReadableExpressions) ([licencí MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí stromu výrazů jako C# kódu:</span><span class="sxs-lookup"><span data-stu-id="bd74b-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Čitelný výrazy vizualizéru](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="bd74b-112">[Vizualizéru stromu výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencí MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, její vlastnosti a související objekty:</span><span class="sxs-lookup"><span data-stu-id="bd74b-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![ExpressionToString vizualizéru](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="bd74b-114">Chcete-li otevřít vizualizér pro strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="bd74b-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="bd74b-115">Klikněte na ikonu lupy, které se zobrazí vedle stromu výrazů v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna.</span><span class="sxs-lookup"><span data-stu-id="bd74b-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="bd74b-116">Zobrazí seznam k dispozici vizualizéry.:</span><span class="sxs-lookup"><span data-stu-id="bd74b-116">A list of available visualizers is displayed.:</span></span> 

      ![Otevírání vizualizéry ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="bd74b-118">Klikněte na vizualizaci, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="bd74b-118">Click the visualizer you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd74b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd74b-119">See also</span></span>

- [<span data-ttu-id="bd74b-120">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="bd74b-120">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="bd74b-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd74b-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="bd74b-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="bd74b-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="bd74b-123">`DebugView` Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd74b-123">`DebugView` syntax</span></span>](debugview-syntax.md)
