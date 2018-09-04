---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: dd3008ffd1364eec3938053bd7d37f95b8a1ebc0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509620"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="84773-102">Ladění stromů výrazů v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="84773-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="84773-103">Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="84773-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="84773-104">Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která je k dispozici pouze v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="84773-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="84773-105">Další informace o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="84773-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="84773-106">Pro lepší reprezentaci obsah stromů výrazů `DebugView` vlastnost používá Visual Studio vizualizéry.</span><span class="sxs-lookup"><span data-stu-id="84773-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="84773-107">Další informace najdete v tématu [vytvořit vlastní Vizualizéry](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="84773-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="84773-108">Chcete-li otevřít vizualizér pro strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="84773-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="84773-109">Klikněte na ikonu lupy, která se zobrazí vedle `DebugView` vlastnost strom výrazu v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **Lokální** okna.</span><span class="sxs-lookup"><span data-stu-id="84773-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="84773-110">Zobrazí se seznam vizualizéry.</span><span class="sxs-lookup"><span data-stu-id="84773-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="84773-111">Klikněte na vizualizaci, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="84773-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="84773-112">Každý typ výrazu se zobrazí ve vizualizátoru, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="84773-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="84773-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="84773-113">ParameterExpressions</span></span>  
 <span data-ttu-id="84773-114"><xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="84773-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="84773-115">Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="84773-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="84773-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="84773-116">Examples</span></span>  
  
|<span data-ttu-id="84773-117">Výraz</span><span class="sxs-lookup"><span data-stu-id="84773-117">Expression</span></span>|<span data-ttu-id="84773-118">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84773-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="84773-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="84773-119">ConstantExpressions</span></span>  
 <span data-ttu-id="84773-120">Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="84773-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="84773-121">Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona k hodnotě.</span><span class="sxs-lookup"><span data-stu-id="84773-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="84773-122">V následující tabulce jsou uvedeny přípony spojené s různé číselné typy.</span><span class="sxs-lookup"><span data-stu-id="84773-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="84773-123">Typ</span><span class="sxs-lookup"><span data-stu-id="84773-123">Type</span></span>|<span data-ttu-id="84773-124">Přípona</span><span class="sxs-lookup"><span data-stu-id="84773-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="84773-125">U</span><span class="sxs-lookup"><span data-stu-id="84773-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="84773-126">L</span><span class="sxs-lookup"><span data-stu-id="84773-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="84773-127">UL</span><span class="sxs-lookup"><span data-stu-id="84773-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="84773-128">D</span><span class="sxs-lookup"><span data-stu-id="84773-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="84773-129">F</span><span class="sxs-lookup"><span data-stu-id="84773-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="84773-130">M</span><span class="sxs-lookup"><span data-stu-id="84773-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="84773-131">Příklady</span><span class="sxs-lookup"><span data-stu-id="84773-131">Examples</span></span>  
  
|<span data-ttu-id="84773-132">Výraz</span><span class="sxs-lookup"><span data-stu-id="84773-132">Expression</span></span>|<span data-ttu-id="84773-133">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84773-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="84773-134">10</span><span class="sxs-lookup"><span data-stu-id="84773-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="84773-135">10D</span><span class="sxs-lookup"><span data-stu-id="84773-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="84773-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="84773-136">BlockExpression</span></span>  
 <span data-ttu-id="84773-137">Pokud typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typu posledního výrazu v bloku, zobrazí se v typu `DebugInfo` vlastnost v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="84773-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="84773-138">V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="84773-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="84773-139">Příklady</span><span class="sxs-lookup"><span data-stu-id="84773-139">Examples</span></span>  
  
|<span data-ttu-id="84773-140">Výraz</span><span class="sxs-lookup"><span data-stu-id="84773-140">Expression</span></span>|<span data-ttu-id="84773-141">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84773-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="84773-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="84773-142">LambdaExpression</span></span>  
 <span data-ttu-id="84773-143"><xref:System.Linq.Expressions.LambdaExpression> objekty se zobrazí spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="84773-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="84773-144">Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="84773-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="84773-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="84773-145">Examples</span></span>  
  
|<span data-ttu-id="84773-146">Výraz</span><span class="sxs-lookup"><span data-stu-id="84773-146">Expression</span></span>|<span data-ttu-id="84773-147">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84773-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="84773-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="84773-148">LabelExpression</span></span>  
 <span data-ttu-id="84773-149">Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget> objektu.</span><span class="sxs-lookup"><span data-stu-id="84773-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="84773-150">`.Label` Token označuje začátek popisek.</span><span class="sxs-lookup"><span data-stu-id="84773-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="84773-151">`.LabelTarget` Určuje cílové cíl, který chcete přejít na token.</span><span class="sxs-lookup"><span data-stu-id="84773-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="84773-152">Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="84773-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="84773-153">Příklady</span><span class="sxs-lookup"><span data-stu-id="84773-153">Examples</span></span>  
  
|<span data-ttu-id="84773-154">Výraz</span><span class="sxs-lookup"><span data-stu-id="84773-154">Expression</span></span>|<span data-ttu-id="84773-155">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84773-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="84773-156">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="84773-156">Checked Operators</span></span>  
 <span data-ttu-id="84773-157">Checked operátory se zobrazí symbol "#" před operátor.</span><span class="sxs-lookup"><span data-stu-id="84773-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="84773-158">Například operátor checked sčítání se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="84773-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="84773-159">Příklady</span><span class="sxs-lookup"><span data-stu-id="84773-159">Examples</span></span>  
  
|<span data-ttu-id="84773-160">Výraz</span><span class="sxs-lookup"><span data-stu-id="84773-160">Expression</span></span>|<span data-ttu-id="84773-161">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84773-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="84773-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="84773-162">See Also</span></span>

- [<span data-ttu-id="84773-163">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="84773-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [<span data-ttu-id="84773-164">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="84773-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
- [<span data-ttu-id="84773-165">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="84773-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
