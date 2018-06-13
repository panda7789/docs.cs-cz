---
title: Ladění stromů výrazů v sadě Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 0b3017f2800a2eb7332028b9cfe6ed9877222087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340067"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="b08bd-102">Ladění stromů výrazů v sadě Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="b08bd-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="b08bd-103">Při ladění aplikace můžete analyzovat struktuře a obsahu stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="b08bd-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="b08bd-104">Chcete-li získat rychlý přehled o výraz stromová struktura, můžete použít `DebugView` vlastnost, která je k dispozici pouze v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="b08bd-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="b08bd-105">Další informace o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="b08bd-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="b08bd-106">Lépe představují obsah stromů výrazů `DebugView` vlastnost používá vizualizérech Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b08bd-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="b08bd-107">Další informace najdete v tématu [vytvořit vlastní Vizualizérech](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="b08bd-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="b08bd-108">Chcete-li otevřít vizualizér pro strom výrazu se nezdařilo</span><span class="sxs-lookup"><span data-stu-id="b08bd-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="b08bd-109">Klikněte na ikonu lupy, který se zobrazí vedle `DebugView` vlastnost strom výrazu v **datatips –**, **sledovat** okně **automobily** okno, nebo **Místní hodnoty –** okno.</span><span class="sxs-lookup"><span data-stu-id="b08bd-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="b08bd-110">Zobrazí se seznam vizualizérech.</span><span class="sxs-lookup"><span data-stu-id="b08bd-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="b08bd-111">Klikněte na tlačítko vizualizér, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="b08bd-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="b08bd-112">Každý typ výrazu se zobrazí v vizualizér, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="b08bd-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="b08bd-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="b08bd-113">ParameterExpressions</span></span>  
 <span data-ttu-id="b08bd-114"><xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="b08bd-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="b08bd-115">Pokud parametr nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="b08bd-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b08bd-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="b08bd-116">Examples</span></span>  
  
|<span data-ttu-id="b08bd-117">Výraz</span><span class="sxs-lookup"><span data-stu-id="b08bd-117">Expression</span></span>|<span data-ttu-id="b08bd-118">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b08bd-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="b08bd-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="b08bd-119">ConstantExpressions</span></span>  
 <span data-ttu-id="b08bd-120">Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselné hodnoty řetězce, a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="b08bd-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="b08bd-121">Pro číselné typy, které mají standardní přípony jako literály jazyka C# se přidá přípona hodnotě.</span><span class="sxs-lookup"><span data-stu-id="b08bd-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="b08bd-122">V následující tabulce jsou uvedeny přípony spojené s různými číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="b08bd-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="b08bd-123">Typ</span><span class="sxs-lookup"><span data-stu-id="b08bd-123">Type</span></span>|<span data-ttu-id="b08bd-124">Přípona</span><span class="sxs-lookup"><span data-stu-id="b08bd-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="b08bd-125">U</span><span class="sxs-lookup"><span data-stu-id="b08bd-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="b08bd-126">L</span><span class="sxs-lookup"><span data-stu-id="b08bd-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="b08bd-127">UL</span><span class="sxs-lookup"><span data-stu-id="b08bd-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="b08bd-128">D</span><span class="sxs-lookup"><span data-stu-id="b08bd-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="b08bd-129">F</span><span class="sxs-lookup"><span data-stu-id="b08bd-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="b08bd-130">M</span><span class="sxs-lookup"><span data-stu-id="b08bd-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="b08bd-131">Příklady</span><span class="sxs-lookup"><span data-stu-id="b08bd-131">Examples</span></span>  
  
|<span data-ttu-id="b08bd-132">Výraz</span><span class="sxs-lookup"><span data-stu-id="b08bd-132">Expression</span></span>|<span data-ttu-id="b08bd-133">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b08bd-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="b08bd-134">10</span><span class="sxs-lookup"><span data-stu-id="b08bd-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="b08bd-135">10D</span><span class="sxs-lookup"><span data-stu-id="b08bd-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="b08bd-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="b08bd-136">BlockExpression</span></span>  
 <span data-ttu-id="b08bd-137">Pokud se typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typ poslední výrazu v bloku, typ se zobrazí v `DebugInfo` vlastnost v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="b08bd-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="b08bd-138">Jinak typ <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="b08bd-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b08bd-139">Příklady</span><span class="sxs-lookup"><span data-stu-id="b08bd-139">Examples</span></span>  
  
|<span data-ttu-id="b08bd-140">Výraz</span><span class="sxs-lookup"><span data-stu-id="b08bd-140">Expression</span></span>|<span data-ttu-id="b08bd-141">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b08bd-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="b08bd-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="b08bd-142">LambdaExpression</span></span>  
 <span data-ttu-id="b08bd-143"><xref:System.Linq.Expressions.LambdaExpression> Zobrazí se objekty, spolu s jejich typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="b08bd-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="b08bd-144">Pokud výrazu lambda nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="b08bd-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b08bd-145">Příklady</span><span class="sxs-lookup"><span data-stu-id="b08bd-145">Examples</span></span>  
  
|<span data-ttu-id="b08bd-146">Výraz</span><span class="sxs-lookup"><span data-stu-id="b08bd-146">Expression</span></span>|<span data-ttu-id="b08bd-147">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b08bd-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="b08bd-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="b08bd-148">LabelExpression</span></span>  
 <span data-ttu-id="b08bd-149">Pokud zadáte výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, tato hodnota se zobrazí před <xref:System.Linq.Expressions.LabelTarget> objektu.</span><span class="sxs-lookup"><span data-stu-id="b08bd-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="b08bd-150">`.Label` Token označuje začátek popisku.</span><span class="sxs-lookup"><span data-stu-id="b08bd-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="b08bd-151">`.LabelTarget` Token označuje cílovým serverem cíl, který má přejít na.</span><span class="sxs-lookup"><span data-stu-id="b08bd-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="b08bd-152">Pokud štítek nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="b08bd-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b08bd-153">Příklady</span><span class="sxs-lookup"><span data-stu-id="b08bd-153">Examples</span></span>  
  
|<span data-ttu-id="b08bd-154">Výraz</span><span class="sxs-lookup"><span data-stu-id="b08bd-154">Expression</span></span>|<span data-ttu-id="b08bd-155">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b08bd-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="b08bd-156">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="b08bd-156">Checked Operators</span></span>  
 <span data-ttu-id="b08bd-157">Checked operátory se zobrazí symbol "#" před operátor.</span><span class="sxs-lookup"><span data-stu-id="b08bd-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="b08bd-158">Např. operátor sčítání zaškrtnuté je zobrazen jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="b08bd-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b08bd-159">Příklady</span><span class="sxs-lookup"><span data-stu-id="b08bd-159">Examples</span></span>  
  
|<span data-ttu-id="b08bd-160">Výraz</span><span class="sxs-lookup"><span data-stu-id="b08bd-160">Expression</span></span>|<span data-ttu-id="b08bd-161">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b08bd-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="b08bd-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="b08bd-162">See Also</span></span>  
 [<span data-ttu-id="b08bd-163">Stromy výrazů (C#)</span><span class="sxs-lookup"><span data-stu-id="b08bd-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="b08bd-164">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b08bd-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="b08bd-165">Vytvořit vlastní Vizualizérech</span><span class="sxs-lookup"><span data-stu-id="b08bd-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
