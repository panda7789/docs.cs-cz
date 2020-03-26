---
title: Lambda – výrazy
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249666"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="a04a1-102">Lambda – výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a04a1-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="a04a1-103">Výraz *lambda* je funkce nebo podprogram bez názvu, který lze použít všude tam, kde je platný delegát.</span><span class="sxs-lookup"><span data-stu-id="a04a1-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="a04a1-104">Lambda výrazy mohou být funkce nebo podprogramy a může být jednořádkové nebo víceřádkové.</span><span class="sxs-lookup"><span data-stu-id="a04a1-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="a04a1-105">Hodnoty z aktuálního oboru můžete předat výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="a04a1-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="a04a1-106">Příkaz `RemoveHandler` je výjimkou.</span><span class="sxs-lookup"><span data-stu-id="a04a1-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="a04a1-107">Výraz lambda nelze předat pro parametr `RemoveHandler`delegáta aplikace .</span><span class="sxs-lookup"><span data-stu-id="a04a1-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="a04a1-108">Výrazy lambda vytvoříte `Function` pomocí `Sub` klíčového slova nebo, stejně jako vytvoříte standardní funkci nebo podprogram.</span><span class="sxs-lookup"><span data-stu-id="a04a1-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="a04a1-109">Však lambda výrazy jsou zahrnuty v příkazu.</span><span class="sxs-lookup"><span data-stu-id="a04a1-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="a04a1-110">Následující příklad je lambda výraz, který zintenzivňuje jeho argument a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a04a1-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="a04a1-111">Příklad ukazuje jednořádkovou i víceřádkovou syntaxi výrazu lambda pro funkci.</span><span class="sxs-lookup"><span data-stu-id="a04a1-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="a04a1-112">Následující příklad je lambda výraz, který zapisuje hodnotu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a04a1-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="a04a1-113">Příklad ukazuje jednořádkovou i víceřádkovou syntaxi výrazu lambda pro podprogram.</span><span class="sxs-lookup"><span data-stu-id="a04a1-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="a04a1-114">Všimněte si, že v předchozích příkladech lambda výrazy jsou přiřazeny k názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="a04a1-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="a04a1-115">Vždy, když odkazujete na proměnnou, vyvoláte výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="a04a1-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="a04a1-116">Můžete také deklarovat a vyvolat výraz lambda současně, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a04a1-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="a04a1-117">Výraz lambda může být vrácen jako hodnota volání funkce (jak je znázorněno v příkladu v části [Kontext](#context) dále v tomto tématu) nebo předán jako argument parametru, který přebírá typ delegáta, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a04a1-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="a04a1-118">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="a04a1-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="a04a1-119">Syntaxe výrazu lambda se podobá standardní funkci nebo podprogramu.</span><span class="sxs-lookup"><span data-stu-id="a04a1-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="a04a1-120">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a04a1-120">The differences are as follows:</span></span>

- <span data-ttu-id="a04a1-121">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="a04a1-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="a04a1-122">Lambda výrazy nemohou mít modifikátory, například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="a04a1-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="a04a1-123">Jednořádkové funkce lambda nepoužívají `As` klauzuli k označení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="a04a1-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="a04a1-124">Místo toho je typ odvozen z hodnoty, kterou tělo výrazu lambda vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="a04a1-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="a04a1-125">Například pokud je `cust.City = "London"`tělo výrazu lambda , `Boolean`jeho návratový typ je .</span><span class="sxs-lookup"><span data-stu-id="a04a1-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="a04a1-126">Ve víceřádkové funkce lambda můžete buď určit návratový typ pomocí `As` klauzule, nebo vynechat `As` klauzuli tak, aby byl odvozen návratový typ.</span><span class="sxs-lookup"><span data-stu-id="a04a1-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="a04a1-127">Pokud `As` je klauzule vynechána pro víceřádkovou funkci lambda, návratový typ je `Return` odvozen jako dominantní typ ze všech příkazů ve funkci lambda více řádků.</span><span class="sxs-lookup"><span data-stu-id="a04a1-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="a04a1-128">*Dominantní typ* je jedinečný typ, který všechny ostatní typy lze rozšířit.</span><span class="sxs-lookup"><span data-stu-id="a04a1-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="a04a1-129">Pokud tento jedinečný typ nelze určit, dominantní typ je jedinečný typ, který všechny ostatní typy v poli lze zúžit.</span><span class="sxs-lookup"><span data-stu-id="a04a1-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="a04a1-130">Pokud nelze určit ani jeden z těchto jedinečných typů, dominantní typ je `Object`.</span><span class="sxs-lookup"><span data-stu-id="a04a1-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="a04a1-131">V tomto případě, `Option Strict` pokud `On`je nastavena na , dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="a04a1-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="a04a1-132">Pokud například výrazy zadané `Return` do příkazu `Integer`obsahují `Long`hodnoty `Double`typu , a , `Double`výsledné pole je typu .</span><span class="sxs-lookup"><span data-stu-id="a04a1-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="a04a1-133">Oba `Integer` `Long` a `Double` rozšířit `Double`na a pouze .</span><span class="sxs-lookup"><span data-stu-id="a04a1-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="a04a1-134">Proto `Double` je dominantní typ.</span><span class="sxs-lookup"><span data-stu-id="a04a1-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="a04a1-135">Další informace naleznete v [tématu Rozšíření a zúžení převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="a04a1-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="a04a1-136">Tělo jednořádkové funkce musí být výraz, který vrací hodnotu, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="a04a1-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="a04a1-137">Neexistuje žádný `Return` příkaz pro jednořádkové funkce.</span><span class="sxs-lookup"><span data-stu-id="a04a1-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="a04a1-138">Hodnota vrácená jednořádkovou funkcí je hodnota výrazu v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="a04a1-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="a04a1-139">Tělo jednořádkové podprogramu musí být jednořádkové prohlášení.</span><span class="sxs-lookup"><span data-stu-id="a04a1-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="a04a1-140">Jednořádkové funkce a podprogramy `End Function` neobsahují `End Sub` příkaz nebo.</span><span class="sxs-lookup"><span data-stu-id="a04a1-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="a04a1-141">Můžete určit datový typ parametru výrazu lambda pomocí klíčového `As` slova nebo lze odvodit datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="a04a1-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="a04a1-142">Všechny parametry musí mít zadané datové typy nebo všechny musí být odvozeny.</span><span class="sxs-lookup"><span data-stu-id="a04a1-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="a04a1-143">`Optional`a `Paramarray` parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="a04a1-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="a04a1-144">Obecné parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="a04a1-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="a04a1-145">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="a04a1-145">Async Lambdas</span></span>

<span data-ttu-id="a04a1-146">Můžete snadno vytvořit lambda výrazy a příkazy, které zahrnují asynchronní zpracování pomocí klíčová slova [Async](../../../../visual-basic/language-reference/modifiers/async.md) a [Await Operator.](../../../../visual-basic/language-reference/operators/await-operator.md)</span><span class="sxs-lookup"><span data-stu-id="a04a1-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="a04a1-147">Například následující příklad windows forms obsahuje obslužnou rutinu události, `ExampleMethodAsync`která volá a čeká na asynchronní metodu .</span><span class="sxs-lookup"><span data-stu-id="a04a1-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

<span data-ttu-id="a04a1-148">Můžete přidat stejnou obslužnou rutinu události pomocí asynchronní lambda v [AddHandler prohlášení](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a04a1-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="a04a1-149">Chcete-li přidat tuto `Async` obslužnou rutinu, přidejte modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="a04a1-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

<span data-ttu-id="a04a1-150">Další informace o vytváření a používání asynchronních metod naleznete [v tématu Asynchronní programování s async a Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="a04a1-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="a04a1-151">Kontext</span><span class="sxs-lookup"><span data-stu-id="a04a1-151">Context</span></span>

<span data-ttu-id="a04a1-152">Výraz lambda sdílí svůj kontext s oborem, ve kterém je definován.</span><span class="sxs-lookup"><span data-stu-id="a04a1-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="a04a1-153">Má stejná přístupová práva jako jakýkoli kód napsaný v obsahujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="a04a1-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="a04a1-154">To zahrnuje přístup k členským proměnným, `Me`funkcím a subs , a parametrům a místním proměnným v obsahujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="a04a1-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="a04a1-155">Přístup k místním proměnným a parametrům v obsahujícím oboru může přesáhnout dobu životnosti tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="a04a1-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="a04a1-156">Tak dlouho, dokud delegát odkazující na výraz lambda není k dispozici pro uvolňování paměti, přístup k proměnným v původním prostředí je zachována.</span><span class="sxs-lookup"><span data-stu-id="a04a1-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="a04a1-157">V následujícím příkladu `target` je `makeTheGame`proměnná local to , metoda, ve které je definován výraz `playTheGame` lambda.</span><span class="sxs-lookup"><span data-stu-id="a04a1-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="a04a1-158">Všimněte si, že vrácený `takeAGuess` výraz `Main`lambda přiřazený `target`v , má stále přístup k místní proměnné .</span><span class="sxs-lookup"><span data-stu-id="a04a1-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="a04a1-159">Následující příklad ukazuje širokou škálu přístupových práv vnořeného výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="a04a1-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="a04a1-160">Při vrácené lambda výraz `Main` je `aDel`spuštěn z as , přistupuje k těmto prvkům:</span><span class="sxs-lookup"><span data-stu-id="a04a1-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="a04a1-161">Pole třídy, ve které je definováno:`aField`</span><span class="sxs-lookup"><span data-stu-id="a04a1-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="a04a1-162">Vlastnost třídy, ve které je definována:`aProp`</span><span class="sxs-lookup"><span data-stu-id="a04a1-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="a04a1-163">Parametr metody `functionWithNestedLambda`, ve kterém je definován:`level1`</span><span class="sxs-lookup"><span data-stu-id="a04a1-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="a04a1-164">Místní proměnná `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="a04a1-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="a04a1-165">Parametr výrazu lambda, ve kterém je vnořen:`level2`</span><span class="sxs-lookup"><span data-stu-id="a04a1-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="a04a1-166">Převod na typ delegáta</span><span class="sxs-lookup"><span data-stu-id="a04a1-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="a04a1-167">Výraz lambda lze implicitně převést na kompatibilní typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="a04a1-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="a04a1-168">Informace o obecných požadavcích na kompatibilitu naleznete v [tématu Uvolněný převod delegátů](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="a04a1-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="a04a1-169">Například následující příklad kódu ukazuje výraz lambda, který `Func(Of Integer, Boolean)` implicitně převádí nebo odpovídající podpis delegáta.</span><span class="sxs-lookup"><span data-stu-id="a04a1-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="a04a1-170">Následující příklad kódu ukazuje výraz lambda, který `Sub(Of Double, String, Double)` implicitně převádí nebo odpovídající podpis delegáta.</span><span class="sxs-lookup"><span data-stu-id="a04a1-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="a04a1-171">Při přiřazení lambda výrazy delegátům nebo předat jako argumenty procedur, můžete zadat názvy parametrů, ale vynechat jejich datové typy, nechat typy převzaty z delegáta.</span><span class="sxs-lookup"><span data-stu-id="a04a1-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="a04a1-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="a04a1-172">Examples</span></span>

- <span data-ttu-id="a04a1-173">Následující příklad definuje výraz lambda, `True` který vrátí, pokud argument typu hodnoty `False` s možnou hodnotou s možnou hodnotou má přiřazenou hodnotu a pokud je `Nothing`jeho hodnota .</span><span class="sxs-lookup"><span data-stu-id="a04a1-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="a04a1-174">Následující příklad definuje výraz lambda, který vrací index posledního prvku v poli.</span><span class="sxs-lookup"><span data-stu-id="a04a1-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="a04a1-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="a04a1-175">See also</span></span>

- [<span data-ttu-id="a04a1-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="a04a1-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a04a1-177">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a04a1-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a04a1-178">Delegáty</span><span class="sxs-lookup"><span data-stu-id="a04a1-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="a04a1-179">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="a04a1-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="a04a1-180">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="a04a1-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="a04a1-181">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a04a1-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="a04a1-182">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a04a1-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="a04a1-183">Postupy: Vytvoření výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="a04a1-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="a04a1-184">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="a04a1-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
