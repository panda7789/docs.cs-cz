---
title: Ladění stromů výrazů v sadě Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: ff56a10b6c25f3165066edb727829cc460f3e96c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344725"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="4ac5a-102">Ladění stromů výrazů v aplikaci Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ac5a-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="4ac5a-103">Při ladění aplikací můžete analyzovat strukturu a obsah stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="4ac5a-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="4ac5a-104">Chcete-li získat rychlý přehled stromové struktury výrazu, můžete použít vlastnost `DebugView`, která představuje stromy výrazů [pomocí speciální syntaxe](debugview-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="4ac5a-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees [using a special syntax](debugview-syntax.md).</span></span> <span data-ttu-id="4ac5a-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="4ac5a-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Snímek obrazovky nástroj DebugView stromu výrazu](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

<span data-ttu-id="4ac5a-107">Vzhledem k tomu, že `DebugView` je řetězec, můžete k jeho zobrazení na více řádcích použít [vestavěný Vizualizér textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , a to tak, že vyberete **Vizualizér textu** z ikony lupy vedle `DebugView` popisku.</span><span class="sxs-lookup"><span data-stu-id="4ac5a-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Snímek obrazovky s Vizualizérm textu aplikovaný na výsledky nástroj DebugView](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

<span data-ttu-id="4ac5a-109">Alternativně můžete nainstalovat a používat [vlastní Vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů, například:</span><span class="sxs-lookup"><span data-stu-id="4ac5a-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees, such as:</span></span>

- <span data-ttu-id="4ac5a-110">[Čitelné výrazy](https://github.com/agileobjects/ReadableExpressions) ([licence MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), které jsou k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)) vykreslí strom C# výrazu jako kód:</span><span class="sxs-lookup"><span data-stu-id="4ac5a-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Snímek obrazovky Vizualizér čitelných výrazů](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- <span data-ttu-id="4ac5a-112">[Vizualizér stromu výrazů](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licence MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, jeho vlastností a souvisejících objektů. a lze strom výrazu vykreslit pomocí Visual Basicho kódu:</span><span class="sxs-lookup"><span data-stu-id="4ac5a-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![Snímek obrazovky Vizualizér ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="4ac5a-114">Otevření Vizualizér pro strom výrazu</span><span class="sxs-lookup"><span data-stu-id="4ac5a-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="4ac5a-115">Klikněte na ikonu lupy, která se zobrazí vedle stromu výrazu v části **datatipů**, v okně **kukátka** , okně **Automatické** hodnoty nebo v **místním** okně.</span><span class="sxs-lookup"><span data-stu-id="4ac5a-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
    <span data-ttu-id="4ac5a-116">Zobrazí se seznam dostupných vizualizací.:</span><span class="sxs-lookup"><span data-stu-id="4ac5a-116">A list of available visualizers is displayed.:</span></span> 

    ![Snímek obrazovky uživatele otevírající vizualizace ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. <span data-ttu-id="4ac5a-118">Klikněte na vizualizér, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="4ac5a-118">Click the visualizer you want to use.</span></span>  

## <a name="see-also"></a><span data-ttu-id="4ac5a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ac5a-119">See also</span></span>

- [<span data-ttu-id="4ac5a-120">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ac5a-120">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="4ac5a-121">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ac5a-121">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugger-feature-tour)
- [<span data-ttu-id="4ac5a-122">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="4ac5a-122">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
- [<span data-ttu-id="4ac5a-123">`DebugView` syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ac5a-123">`DebugView` syntax</span></span>](debugview-syntax.md)
