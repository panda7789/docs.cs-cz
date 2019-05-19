---
title: Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 7fc97d898c5956b5a569036e6e0fe1174714576d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879851"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="2c068-102">Ladění stromů výrazů v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c068-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="2c068-103">Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="2c068-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="2c068-104">Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která představuje stromů výrazů pomocí speciální syntaxe popsané [níže](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="2c068-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="2c068-105">(Všimněte si, že `DebugView` je k dispozici pouze v režimu ladění.)</span><span class="sxs-lookup"><span data-stu-id="2c068-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![Nástroj DebugView stromu výrazu v ladicím programu sady Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

<span data-ttu-id="2c068-107">Protože `DebugView` je řetězec, můžete použít [integrované Vizualizátor textu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) zobrazíte na více řádcích, tak, že vyberete **Vizualizátor textu** z ikony lupy vedle `DebugView` Popisek.</span><span class="sxs-lookup"><span data-stu-id="2c068-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Vizualizátor textu použitý k výsledkům 'nástroj DebugView.](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

<span data-ttu-id="2c068-109">Alternativně můžete nainstalovat a používat [vlastní vizualizér](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) pro stromy výrazů:</span><span class="sxs-lookup"><span data-stu-id="2c068-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="2c068-110">[Čitelný výrazy](https://github.com/agileobjects/ReadableExpressions) ([licencí MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), k dispozici na [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), vykreslí stromu výrazů jako C# kódu:</span><span class="sxs-lookup"><span data-stu-id="2c068-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Čitelný výrazy vizualizéru](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="2c068-112">[Vizualizéru stromu výrazu](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencí MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), poskytuje grafické zobrazení stromu výrazů, vlastnosti a související objekty; a může mít za následek stromu výrazů kódu jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="2c068-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects; and can render the expression tree using Visual Basic code:</span></span>

  ![ExpressionToString vizualizéru](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="2c068-114">Chcete-li otevřít vizualizér pro strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="2c068-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="2c068-115">Klikněte na ikonu lupy, které se zobrazí vedle stromu výrazů v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **lokální** okna.</span><span class="sxs-lookup"><span data-stu-id="2c068-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="2c068-116">Zobrazí seznam k dispozici vizualizéry.:</span><span class="sxs-lookup"><span data-stu-id="2c068-116">A list of available visualizers is displayed.:</span></span> 

      ![Otevírání vizualizéry ze sady Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. <span data-ttu-id="2c068-118">Klikněte na vizualizaci, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="2c068-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="2c068-119">`DebugView` Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c068-119">`DebugView` syntax</span></span> 

<span data-ttu-id="2c068-120">Každý typ výrazu se zobrazí ve vizualizátoru, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="2c068-120">Each expression type is displayed in the visualizer as described in the following sections.</span></span>

## <a name="parameterexpressions"></a><span data-ttu-id="2c068-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="2c068-121">ParameterExpressions</span></span>

<span data-ttu-id="2c068-122"><xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="2c068-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="2c068-123">Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="2c068-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="2c068-124">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c068-124">Examples</span></span>

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    <span data-ttu-id="2c068-125">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-125">`DebugView` property</span></span>

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    <span data-ttu-id="2c068-126">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-126">`DebugView` property</span></span>

    `$var1`

## <a name="constantexpressions"></a><span data-ttu-id="2c068-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="2c068-127">ConstantExpressions</span></span>
 <span data-ttu-id="2c068-128">Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="2c068-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="2c068-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c068-129">Examples</span></span>

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="2c068-130">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-130">`DebugView` property</span></span>

    <span data-ttu-id="2c068-131">10</span><span class="sxs-lookup"><span data-stu-id="2c068-131">10</span></span>

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="2c068-132">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-132">`DebugView` property</span></span>

    <span data-ttu-id="2c068-133">10D</span><span class="sxs-lookup"><span data-stu-id="2c068-133">10D</span></span>

## <a name="blockexpression"></a><span data-ttu-id="2c068-134">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="2c068-134">BlockExpression</span></span>

<span data-ttu-id="2c068-135">Pokud typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typu posledního výrazu v bloku, zobrazí se v typu `DebugInfo` vlastnost v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="2c068-135">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="2c068-136">V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="2c068-136">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="2c068-137">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c068-137">Examples</span></span>

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    <span data-ttu-id="2c068-138">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-138">`DebugView` property</span></span>

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    <span data-ttu-id="2c068-139">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-139">`DebugView` property</span></span>

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a><span data-ttu-id="2c068-140">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="2c068-140">LambdaExpression</span></span>

<span data-ttu-id="2c068-141"><xref:System.Linq.Expressions.LambdaExpression> objekty se zobrazí spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="2c068-141"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="2c068-142">Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="2c068-142">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="2c068-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c068-143">Examples</span></span>

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    <span data-ttu-id="2c068-144">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-144">`DebugView` property</span></span>

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    <span data-ttu-id="2c068-145">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-145">`DebugView` property</span></span>

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a><span data-ttu-id="2c068-146">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="2c068-146">LabelExpression</span></span>

<span data-ttu-id="2c068-147">Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget> objektu.</span><span class="sxs-lookup"><span data-stu-id="2c068-147">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="2c068-148">`.Label` Token označuje začátek popisek.</span><span class="sxs-lookup"><span data-stu-id="2c068-148">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="2c068-149">`.LabelTarget` Určuje cílové cíl, který chcete přejít na token.</span><span class="sxs-lookup"><span data-stu-id="2c068-149">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="2c068-150">Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="2c068-150">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="2c068-151">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c068-151">Examples</span></span>

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    <span data-ttu-id="2c068-152">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-152">`DebugView` property</span></span>

    `.Block() {`

    `.Goto SampleLabel { 0 };`

    `.Label`

    `-1`

    `.LabelTarget SampleLabel:`

    `}`

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label()
    Dim block As BlockExpression = Expression.Block(
    Expression.Goto(target), Expression.Label(target))
    ```

    <span data-ttu-id="2c068-153">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-153">`DebugView` property</span></span>

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a><span data-ttu-id="2c068-154">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="2c068-154">Checked Operators</span></span>

<span data-ttu-id="2c068-155">Checked operátory se zobrazí symbol "#" před operátor.</span><span class="sxs-lookup"><span data-stu-id="2c068-155">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="2c068-156">Například operátor checked sčítání se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="2c068-156">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="2c068-157">Příklady</span><span class="sxs-lookup"><span data-stu-id="2c068-157">Examples</span></span>

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    <span data-ttu-id="2c068-158">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-158">`DebugView` property</span></span>

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    <span data-ttu-id="2c068-159">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2c068-159">`DebugView` property</span></span>

    `#(System.Int32)10D`

## <a name="see-also"></a><span data-ttu-id="2c068-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c068-160">See also</span></span>

- [<span data-ttu-id="2c068-161">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2c068-161">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="2c068-162">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c068-162">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="2c068-163">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="2c068-163">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
