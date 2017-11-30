---
title: "Ladění stromů výrazů v sadě Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff1bee9c3c3fdeafab24368d2c7e8376d4ff7b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="77996-102">Ladění stromů výrazů v sadě Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77996-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="77996-103">Při ladění aplikace můžete analyzovat struktuře a obsahu stromů výrazů.</span><span class="sxs-lookup"><span data-stu-id="77996-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="77996-104">Chcete-li získat rychlý přehled o výraz stromová struktura, můžete použít `DebugView` vlastnost, která je k dispozici pouze v režimu ladění.</span><span class="sxs-lookup"><span data-stu-id="77996-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="77996-105">Další informace o ladění najdete v tématu [ladění v sadě Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="77996-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="77996-106">Lépe představují obsah stromů výrazů `DebugView` vlastnost používá vizualizérech Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="77996-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="77996-107">Další informace najdete v tématu [vytvořit vlastní Vizualizérech](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="77996-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="77996-108">Chcete-li otevřít vizualizér pro strom výrazu se nezdařilo</span><span class="sxs-lookup"><span data-stu-id="77996-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="77996-109">Klikněte na ikonu lupy, který se zobrazí vedle `DebugView` vlastnost strom výrazu v **datatips –**, **sledovat** okně **automobily** okno, nebo **Místní hodnoty –** okno.</span><span class="sxs-lookup"><span data-stu-id="77996-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="77996-110">Zobrazí se seznam vizualizérech.</span><span class="sxs-lookup"><span data-stu-id="77996-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="77996-111">Klikněte na tlačítko vizualizér, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="77996-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="77996-112">Každý typ výrazu se zobrazí v vizualizér, jak je popsáno v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="77996-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="77996-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="77996-113">ParameterExpressions</span></span>  
 <span data-ttu-id="77996-114"><xref:System.Linq.Expressions.ParameterExpression>názvy proměnných jsou zobrazeny symbolem "$" na začátku.</span><span class="sxs-lookup"><span data-stu-id="77996-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="77996-115">Pokud parametr nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `$var1` nebo `$var2`.</span><span class="sxs-lookup"><span data-stu-id="77996-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="77996-116">Příklady</span><span class="sxs-lookup"><span data-stu-id="77996-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="77996-117">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="77996-118">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="77996-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="77996-119">ConstantExpressions</span></span>  
 <span data-ttu-id="77996-120">Pro <xref:System.Linq.Expressions.ConstantExpression> objekty, které představují celočíselné hodnoty řetězce, a `null`, zobrazí se hodnota konstanty.</span><span class="sxs-lookup"><span data-stu-id="77996-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="77996-121">Příklady</span><span class="sxs-lookup"><span data-stu-id="77996-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="77996-122">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="77996-123">10</span><span class="sxs-lookup"><span data-stu-id="77996-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="77996-124">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="77996-125">10D</span><span class="sxs-lookup"><span data-stu-id="77996-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="77996-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="77996-126">BlockExpression</span></span>  
 <span data-ttu-id="77996-127">Pokud se typ <xref:System.Linq.Expressions.BlockExpression> objektu se liší od typ poslední výrazu v bloku, typ se zobrazí v `DebugInfo` vlastnost v lomených závorkách (\< a >).</span><span class="sxs-lookup"><span data-stu-id="77996-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="77996-128">Jinak typ <xref:System.Linq.Expressions.BlockExpression> objekt se nezobrazí.</span><span class="sxs-lookup"><span data-stu-id="77996-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="77996-129">Příklady</span><span class="sxs-lookup"><span data-stu-id="77996-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="77996-130">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="77996-131">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="77996-132">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="77996-132">LambdaExpression</span></span>  
 <span data-ttu-id="77996-133"><xref:System.Linq.Expressions.LambdaExpression>Zobrazí se objekty, spolu s jejich typů delegátů.</span><span class="sxs-lookup"><span data-stu-id="77996-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="77996-134">Pokud výrazu lambda nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Lambda1` nebo `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="77996-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="77996-135">Příklady</span><span class="sxs-lookup"><span data-stu-id="77996-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="77996-136">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="77996-137">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="77996-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="77996-138">LabelExpression</span></span>  
 <span data-ttu-id="77996-139">Pokud zadáte výchozí hodnotu pro <xref:System.Linq.Expressions.LabelExpression> objektu, tato hodnota se zobrazí před <xref:System.Linq.Expressions.LabelTarget> objektu.</span><span class="sxs-lookup"><span data-stu-id="77996-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="77996-140">`.Label` Token označuje začátek popisku.</span><span class="sxs-lookup"><span data-stu-id="77996-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="77996-141">`.LabelTarget` Token označuje cílovým serverem cíl, který má přejít na.</span><span class="sxs-lookup"><span data-stu-id="77996-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="77996-142">Pokud štítek nemá název, je přiřazen automaticky vygenerovaným názvem, jako například `#Label1` nebo `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="77996-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="77996-143">Příklady</span><span class="sxs-lookup"><span data-stu-id="77996-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="77996-144">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="77996-145">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="77996-146">Checked operátory</span><span class="sxs-lookup"><span data-stu-id="77996-146">Checked Operators</span></span>  
 <span data-ttu-id="77996-147">Checked operátory se zobrazí symbol "#" před operátor.</span><span class="sxs-lookup"><span data-stu-id="77996-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="77996-148">Např. operátor sčítání zaškrtnuté je zobrazen jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="77996-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="77996-149">Příklady</span><span class="sxs-lookup"><span data-stu-id="77996-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="77996-150">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="77996-151">`DebugView`Vlastnost</span><span class="sxs-lookup"><span data-stu-id="77996-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="77996-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="77996-152">See Also</span></span>  
 [<span data-ttu-id="77996-153">Stromy výrazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77996-153">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="77996-154">Ladění v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="77996-154">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="77996-155">Vytvořit vlastní Vizualizérech</span><span class="sxs-lookup"><span data-stu-id="77996-155">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
