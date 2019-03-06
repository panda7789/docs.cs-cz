---
title: Ladění stromů výrazů v sadě Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: fb5905c3c1124dd64371216bddda0a17235abdce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364720"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="03520-102">Ladění stromů výrazů v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03520-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="03520-103">Při ladění aplikací můžete analyzovat struktuře a obsahu stromy výrazů.</span><span class="sxs-lookup"><span data-stu-id="03520-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="03520-104">Pokud chcete získat rychlý přehled toho, stromové struktury výrazu, můžete použít `DebugView` vlastnost, která je k dispozici pouze v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="03520-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="03520-105">Další informace o ladění naleznete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="03520-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>

<span data-ttu-id="03520-106">Pro lepší reprezentaci obsah stromů výrazů `DebugView` vlastnost používá Visual Studio vizualizéry.</span><span class="sxs-lookup"><span data-stu-id="03520-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="03520-107">Další informace najdete v tématu [vytvořit vlastní Vizualizéry](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="03520-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="03520-108">Chcete-li otevřít vizualizér pro strom výrazu.</span><span class="sxs-lookup"><span data-stu-id="03520-108">To open a visualizer for an expression tree</span></span>

1. <span data-ttu-id="03520-109">Klikněte na ikonu lupy, která se zobrazí vedle `DebugView` vlastnost strom výrazu v **DataTips**, **Watch** okně **automatické hodnoty** okna, nebo **Lokální** okna.</span><span class="sxs-lookup"><span data-stu-id="03520-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>

    <span data-ttu-id="03520-110">Zobrazí se seznam vizualizéry.</span><span class="sxs-lookup"><span data-stu-id="03520-110">A list of visualizers is displayed.</span></span>

2. <span data-ttu-id="03520-111">Klikněte na vizualizaci, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="03520-111">Click the visualizer you want to use.</span></span>

<span data-ttu-id="03520-112">Každý typ výrazu se zobrazí ve vizualizátoru, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="03520-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>

## <a name="parameterexpressions"></a><span data-ttu-id="03520-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="03520-113">ParameterExpressions</span></span>

<span data-ttu-id="03520-114"><xref:System.Linq.Expressions.ParameterExpression> názvy proměnných jsou zobrazeny se symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="03520-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>

<span data-ttu-id="03520-115">Pokud parametr nemá název, je přiřazen automaticky vygenerovaný název, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="03520-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>

### <a name="examples"></a><span data-ttu-id="03520-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="03520-116">Examples</span></span>

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer), "num")
    ```

    <span data-ttu-id="03520-117">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-117">`DebugView` property</span></span>

    `$num`

- `Expression`

    ```vb
    Dim numParam As ParameterExpression =
    Expression.Parameter(GetType(Integer))
    ```

    <span data-ttu-id="03520-118">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-118">`DebugView` property</span></span>

    `$var1`

## <a name="constantexpressions"></a><span data-ttu-id="03520-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="03520-119">ConstantExpressions</span></span>
 <span data-ttu-id="03520-120">Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselných hodnot, řetězce a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="03520-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="03520-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="03520-121">Examples</span></span>

- `Expression`

    ```vb
    Dim num as Integer= 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="03520-122">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-122">`DebugView` property</span></span>

    <span data-ttu-id="03520-123">10</span><span class="sxs-lookup"><span data-stu-id="03520-123">10</span></span>

- `Expression`

    ```vb
    Dim num As Double = 10
    Dim expr As ConstantExpression = Expression.Constant(num)
    ```

    <span data-ttu-id="03520-124">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-124">`DebugView` property</span></span>

    <span data-ttu-id="03520-125">10D</span><span class="sxs-lookup"><span data-stu-id="03520-125">10D</span></span>

## <a name="blockexpression"></a><span data-ttu-id="03520-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="03520-126">BlockExpression</span></span>

<span data-ttu-id="03520-127">Pokud typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typu posledního výrazu v bloku, zobrazí se v typu `DebugInfo` vlastnost v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="03520-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="03520-128">V opačném případě typu <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="03520-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>

### <a name="examples"></a><span data-ttu-id="03520-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="03520-129">Examples</span></span>

- `Expression`

    ```vb
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))
    ```

    <span data-ttu-id="03520-130">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-130">`DebugView` property</span></span>

    `.Block() {`

    `"test"`

    `}`

- `Expression`

    ```vb
    Dim block As BlockExpression =
    Expression.Block(GetType(Object), Expression.Constant("test"))
    ```

    <span data-ttu-id="03520-131">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-131">`DebugView` property</span></span>

    `.Block<System.Object>() {`

    `"test"`

    `}`

## <a name="lambdaexpression"></a><span data-ttu-id="03520-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="03520-132">LambdaExpression</span></span>

<span data-ttu-id="03520-133"><xref:System.Linq.Expressions.LambdaExpression> objekty se zobrazí spolu s jejich typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="03520-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>

<span data-ttu-id="03520-134">Pokud výraz lambda nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="03520-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>

### <a name="examples"></a><span data-ttu-id="03520-135">Příklady</span><span class="sxs-lookup"><span data-stu-id="03520-135">Examples</span></span>

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))
    ```

    <span data-ttu-id="03520-136">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-136">`DebugView` property</span></span>

    `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`

    `1`

    `}`

- `Expression`

    ```vb
    Dim lambda As LambdaExpression =
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLambda", Nothing)
    ```

    <span data-ttu-id="03520-137">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-137">`DebugView` property</span></span>

    `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`

    `1`

    `}`

## <a name="labelexpression"></a><span data-ttu-id="03520-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="03520-138">LabelExpression</span></span>

<span data-ttu-id="03520-139">Pokud chcete zadat výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, zobrazí se tato hodnota před <xref:System.Linq.Expressions.LabelTarget> objektu.</span><span class="sxs-lookup"><span data-stu-id="03520-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>

<span data-ttu-id="03520-140">`.Label` Token označuje začátek popisek.</span><span class="sxs-lookup"><span data-stu-id="03520-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="03520-141">`.LabelTarget` Určuje cílové cíl, který chcete přejít na token.</span><span class="sxs-lookup"><span data-stu-id="03520-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>

<span data-ttu-id="03520-142">Pokud popisek nemá název, je přiřazen automaticky vygenerovaný název, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="03520-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>

### <a name="examples"></a><span data-ttu-id="03520-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="03520-143">Examples</span></span>

- `Expression`

    ```vb
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")
    Dim label1 As BlockExpression = Expression.Block(
    Expression.Goto(target, Expression.Constant(0)),
    Expression.Label(target, Expression.Constant(-1)))
    ```

    <span data-ttu-id="03520-144">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-144">`DebugView` property</span></span>

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

    <span data-ttu-id="03520-145">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-145">`DebugView` property</span></span>

    `.Block() {`

    `.Goto #Label1 { };`

    `.Label`

    `.LabelTarget #Label1:`

    `}`

## <a name="checked-operators"></a><span data-ttu-id="03520-146">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="03520-146">Checked Operators</span></span>

<span data-ttu-id="03520-147">Checked operátory se zobrazí symbol "#" před operátor.</span><span class="sxs-lookup"><span data-stu-id="03520-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="03520-148">Například operátor checked sčítání se zobrazí jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="03520-148">For example, the checked addition operator is displayed as `#+`.</span></span>

### <a name="examples"></a><span data-ttu-id="03520-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="03520-149">Examples</span></span>

- `Expression`

    ```vb
    Dim expr As Expression = Expression.AddChecked(
    Expression.Constant(1), Expression.Constant(2))
    ```

    <span data-ttu-id="03520-150">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-150">`DebugView` property</span></span>

    `1 #+ 2`

- `Expression`

    ```vb
    Dim expr As Expression = Expression.ConvertChecked(
    Expression.Constant(10.0), GetType(Integer))
    ```

    <span data-ttu-id="03520-151">`DebugView` Vlastnost</span><span class="sxs-lookup"><span data-stu-id="03520-151">`DebugView` property</span></span>

    `#(System.Int32)10D`

## <a name="see-also"></a><span data-ttu-id="03520-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03520-152">See also</span></span>

- [<span data-ttu-id="03520-153">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03520-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="03520-154">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03520-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="03520-155">Vytváření vlastních vizualizérů</span><span class="sxs-lookup"><span data-stu-id="03520-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
