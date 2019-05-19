---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877176"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="14239-102">Ladění stromů výrazů v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="14239-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="14239-103">Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="14239-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="14239-104">Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromů výrazů pomocí speciální syntaxe popsané [níže](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="14239-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="14239-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="14239-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="14239-107">Protože `DebugView` je řetězec, můžete použít [integrované Vizualizátor textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) zobrazíte na více řádcích, tak, že vyberete **Vizualizátor textu** z ikony lupy vedle `DebugView` Popisek.</span><span class="sxs-lookup"><span data-stu-id="14239-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Vizualizátor textu použitý k výsledkům 'nástroj DebugView.](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="14239-109">Alternativně můžete nainstalovat a používat [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů:</span><span class="sxs-lookup"><span data-stu-id="14239-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="14239-110">[Čitelný výrazy](https://github.com/agileobjects/ReadableExpressions) ([licencí MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí stromu výrazů jako C# kódu:</span><span class="sxs-lookup"><span data-stu-id="14239-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Čitelný výrazy vizualizéru](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="14239-112">[Vizualizéru stromu výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencí MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, její vlastnosti a související objekty:</span><span class="sxs-lookup"><span data-stu-id="14239-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![ExpressionToString vizualizéru](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="14239-114">Chcete-li otevřít vizualizér pro strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="14239-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="14239-115">Klikněte na ikonu lupy, které se zobrazí vedle stromu výrazů v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna.</span><span class="sxs-lookup"><span data-stu-id="14239-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="14239-116">Zobrazí seznam k dispozici vizualizéry.:</span><span class="sxs-lookup"><span data-stu-id="14239-116">A list of available visualizers is displayed.:</span></span> 

      ![Otevírání vizualizéry ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="14239-118">Klikněte na vizualizaci, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="14239-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="14239-119">`DebugView` Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14239-119">`DebugView` syntax</span></span> 

<span data-ttu-id="14239-120">Každý typ výrazu se zobrazí `DebugView` vlastnost, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="14239-120">Each expression type is displayed by the `DebugView` property as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="14239-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="14239-121">ParameterExpressions</span></span>  
 <span data-ttu-id="14239-122"><xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="14239-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="14239-123">Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="14239-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="14239-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="14239-124">Examples</span></span>  
  
|<span data-ttu-id="14239-125">Výraz</span><span class="sxs-lookup"><span data-stu-id="14239-125">Expression</span></span>|<span data-ttu-id="14239-126">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="14239-126">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="14239-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="14239-127">ConstantExpressions</span></span>  
 <span data-ttu-id="14239-128">Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="14239-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="14239-129">Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona k hodnotě.</span><span class="sxs-lookup"><span data-stu-id="14239-129">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="14239-130">V následující tabulce jsou uvedeny přípony spojené s různé číselné typy.</span><span class="sxs-lookup"><span data-stu-id="14239-130">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="14239-131">Type</span><span class="sxs-lookup"><span data-stu-id="14239-131">Type</span></span>|<span data-ttu-id="14239-132">Přípona</span><span class="sxs-lookup"><span data-stu-id="14239-132">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="14239-133">U</span><span class="sxs-lookup"><span data-stu-id="14239-133">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="14239-134">L</span><span class="sxs-lookup"><span data-stu-id="14239-134">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="14239-135">UL</span><span class="sxs-lookup"><span data-stu-id="14239-135">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="14239-136">D</span><span class="sxs-lookup"><span data-stu-id="14239-136">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="14239-137">F</span><span class="sxs-lookup"><span data-stu-id="14239-137">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="14239-138">M</span><span class="sxs-lookup"><span data-stu-id="14239-138">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="14239-139">Příklady</span><span class="sxs-lookup"><span data-stu-id="14239-139">Examples</span></span>  
  
|<span data-ttu-id="14239-140">Výraz</span><span class="sxs-lookup"><span data-stu-id="14239-140">Expression</span></span>|<span data-ttu-id="14239-141">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="14239-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="14239-142">10</span><span class="sxs-lookup"><span data-stu-id="14239-142">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="14239-143">10D</span><span class="sxs-lookup"><span data-stu-id="14239-143">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="14239-144">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="14239-144">BlockExpression</span></span>  
 <span data-ttu-id="14239-145">Pokud typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typu posledního výrazu v bloku, zobrazí se v typu `DebugInfo` vlastnost v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="14239-145">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="14239-146">V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="14239-146">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="14239-147">Příklady</span><span class="sxs-lookup"><span data-stu-id="14239-147">Examples</span></span>  
  
|<span data-ttu-id="14239-148">Výraz</span><span class="sxs-lookup"><span data-stu-id="14239-148">Expression</span></span>|<span data-ttu-id="14239-149">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="14239-149">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="14239-150">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="14239-150">LambdaExpression</span></span>  
 <span data-ttu-id="14239-151"><xref:System.Linq.Expressions.LambdaExpression> objekty se zobrazí spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="14239-151"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="14239-152">Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="14239-152">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="14239-153">Příklady</span><span class="sxs-lookup"><span data-stu-id="14239-153">Examples</span></span>  
  
|<span data-ttu-id="14239-154">Výraz</span><span class="sxs-lookup"><span data-stu-id="14239-154">Expression</span></span>|<span data-ttu-id="14239-155">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="14239-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="14239-156">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="14239-156">LabelExpression</span></span>  
 <span data-ttu-id="14239-157">Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget> objektu.</span><span class="sxs-lookup"><span data-stu-id="14239-157">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="14239-158">`.Label` Token označuje začátek popisek.</span><span class="sxs-lookup"><span data-stu-id="14239-158">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="14239-159">`.LabelTarget` Určuje cílové cíl, který chcete přejít na token.</span><span class="sxs-lookup"><span data-stu-id="14239-159">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="14239-160">Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="14239-160">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="14239-161">Příklady</span><span class="sxs-lookup"><span data-stu-id="14239-161">Examples</span></span>  
  
|<span data-ttu-id="14239-162">Výraz</span><span class="sxs-lookup"><span data-stu-id="14239-162">Expression</span></span>|<span data-ttu-id="14239-163">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="14239-163">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="14239-164">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="14239-164">Checked Operators</span></span>  
 <span data-ttu-id="14239-165">Checked operátory se zobrazí symbol "#" před operátor.</span><span class="sxs-lookup"><span data-stu-id="14239-165">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="14239-166">Například operátor checked sčítání se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="14239-166">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="14239-167">Příklady</span><span class="sxs-lookup"><span data-stu-id="14239-167">Examples</span></span>  
  
|<span data-ttu-id="14239-168">Výraz</span><span class="sxs-lookup"><span data-stu-id="14239-168">Expression</span></span>|<span data-ttu-id="14239-169">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="14239-169">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="14239-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14239-170">See also</span></span>

- [<span data-ttu-id="14239-171">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="14239-171">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="14239-172">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="14239-172">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="14239-173">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="14239-173">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
