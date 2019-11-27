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
ms.openlocfilehash: f3f963167e1b3633cc5fe6e1f435e374cd272cce
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345979"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="7de3b-102">Lambda – výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7de3b-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="7de3b-103">*Výraz lambda* je funkce nebo podrutina bez názvu, který lze použít všude, kde je delegát platný.</span><span class="sxs-lookup"><span data-stu-id="7de3b-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="7de3b-104">Výrazy lambda mohou být funkce nebo podprocesy a mohou být jednořádkové nebo víceřádkové.</span><span class="sxs-lookup"><span data-stu-id="7de3b-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="7de3b-105">Můžete předat hodnoty z aktuálního oboru do výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="7de3b-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="7de3b-106">Příkaz `RemoveHandler` je výjimka.</span><span class="sxs-lookup"><span data-stu-id="7de3b-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="7de3b-107">Do parametru Delegate `RemoveHandler`nelze předat výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="7de3b-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="7de3b-108">Lambda výrazy vytvoříte pomocí klíčového slova `Function` nebo `Sub` stejným způsobem jako při vytváření standardní funkce nebo podrutiny.</span><span class="sxs-lookup"><span data-stu-id="7de3b-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="7de3b-109">Výrazy lambda jsou však zahrnuty v příkazu.</span><span class="sxs-lookup"><span data-stu-id="7de3b-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="7de3b-110">Následující příklad je výraz lambda, který zvyšuje svůj argument a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7de3b-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="7de3b-111">V příkladu se zobrazí jak jednoduchá čára, tak víceřádková syntaxe výrazu lambda pro funkci.</span><span class="sxs-lookup"><span data-stu-id="7de3b-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="7de3b-112">Následující příklad je výraz lambda, který zapisuje hodnotu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7de3b-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="7de3b-113">V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro podprogram.</span><span class="sxs-lookup"><span data-stu-id="7de3b-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="7de3b-114">Všimněte si, že v předchozích příkladech jsou výrazy lambda přiřazeny názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="7de3b-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="7de3b-115">Vždy, když odkazujete na proměnnou, vyvoláte výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="7de3b-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="7de3b-116">Můžete také deklarovat a vyvolat výraz lambda ve stejnou dobu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7de3b-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="7de3b-117">Výraz lambda lze vrátit jako hodnotu volání funkce (jak je uvedeno v příkladu v [kontextu](#context) dále v tomto tématu), nebo předaný jako argument parametru, který přebírá typ delegáta, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7de3b-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="7de3b-118">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="7de3b-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="7de3b-119">Syntaxe výrazu lambda se podobá funkci standardní funkce nebo dílčí rutiny.</span><span class="sxs-lookup"><span data-stu-id="7de3b-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="7de3b-120">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7de3b-120">The differences are as follows:</span></span>

- <span data-ttu-id="7de3b-121">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="7de3b-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="7de3b-122">Výrazy lambda nemůžou mít modifikátory, jako je `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="7de3b-123">Jednořádkové funkce lambda nepoužívají klauzuli `As` k určení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="7de3b-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="7de3b-124">Místo toho je typ odvozen z hodnoty, na kterou je text výrazu lambda vyhodnocen.</span><span class="sxs-lookup"><span data-stu-id="7de3b-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="7de3b-125">Například pokud je tělo výrazu lambda `cust.City = "London"`, je jeho návratový typ `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="7de3b-126">Ve víceřádkových lambda funkcích můžete buď zadat návratový typ pomocí klauzule `As`, nebo vynechat klauzuli `As`, aby se návratový typ odvodil.</span><span class="sxs-lookup"><span data-stu-id="7de3b-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="7de3b-127">Pokud je u víceřádkové funkce lambda vynechána klauzule `As`, návratový typ je odvozený jako dominantní typ ze všech příkazů `Return` ve víceřádkové funkci lambda.</span><span class="sxs-lookup"><span data-stu-id="7de3b-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="7de3b-128">*Dominantní typ* je jedinečný typ, na který se mohou rozšířit všechny ostatní typy.</span><span class="sxs-lookup"><span data-stu-id="7de3b-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="7de3b-129">Pokud tento jedinečný typ nelze určit, dominantní typ je jedinečný typ, který mohou být pro všechny ostatní typy v poli zúženy.</span><span class="sxs-lookup"><span data-stu-id="7de3b-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="7de3b-130">Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="7de3b-131">V takovém případě, pokud je `Option Strict` nastaveno na `On`, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="7de3b-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="7de3b-132">Například pokud výrazy dodané do příkazu `Return` obsahují hodnoty typu `Integer`, `Long`a `Double`, výsledné pole je typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="7de3b-133">`Integer` i `Long` rozšířit na `Double` a pouze `Double`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="7de3b-134">Proto je `Double` dominantní typ.</span><span class="sxs-lookup"><span data-stu-id="7de3b-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="7de3b-135">Další informace najdete v tématu [rozšiřování a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="7de3b-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="7de3b-136">Tělo funkce s jednou řádkou musí být výraz, který vrací hodnotu, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="7de3b-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="7de3b-137">Pro jednořádkové funkce není k dispozici žádný příkaz `Return`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="7de3b-138">Hodnota vrácená funkcí single-line je hodnota výrazu v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="7de3b-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="7de3b-139">Tělo jednořádkového podprocesu musí být jednořádkový příkaz.</span><span class="sxs-lookup"><span data-stu-id="7de3b-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="7de3b-140">Jednořádkové funkce a podprogramy neobsahují příkaz `End Function` ani `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="7de3b-141">Můžete zadat datový typ parametru výrazu lambda pomocí klíčového slova `As`, nebo datový typ parametru lze odvodit.</span><span class="sxs-lookup"><span data-stu-id="7de3b-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="7de3b-142">Buď musí mít všechny parametry zadané datové typy, nebo musí být všechny odvoditelné.</span><span class="sxs-lookup"><span data-stu-id="7de3b-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="7de3b-143">parametry `Optional` a `Paramarray` nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="7de3b-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="7de3b-144">Obecné parametry nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="7de3b-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="7de3b-145">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="7de3b-145">Async Lambdas</span></span>

<span data-ttu-id="7de3b-146">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí klíčových slov [Async](../../../../visual-basic/language-reference/modifiers/async.md) a [await](../../../../visual-basic/language-reference/operators/await-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="7de3b-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="7de3b-147">Například následující příklad model Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="7de3b-148">Můžete přidat stejnou obslužnou rutinu události pomocí asynchronní lambda v [příkazu AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7de3b-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="7de3b-149">Chcete-li přidat tuto obslužnou rutinu, přidejte modifikátor `Async` před seznam parametrů lambda, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7de3b-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="7de3b-150">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="7de3b-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="7de3b-151">Kontext</span><span class="sxs-lookup"><span data-stu-id="7de3b-151">Context</span></span>

<span data-ttu-id="7de3b-152">Výraz lambda sdílí svůj kontext s oborem, ve kterém je definován.</span><span class="sxs-lookup"><span data-stu-id="7de3b-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="7de3b-153">Má stejná přístupová práva jako jakýkoli kód napsaný v nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="7de3b-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="7de3b-154">To zahrnuje přístup k proměnným členů, funkcím a předparametrům, `Me`a parametrům a lokálním proměnným v nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="7de3b-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="7de3b-155">Přístup k lokálním proměnným a parametrům v rámci nadřazeného oboru může přesáhnout dobu života tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="7de3b-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="7de3b-156">Dokud nebude delegát odkazující na výraz lambda dostupný pro uvolňování paměti, bude zachován přístup k proměnným v původním prostředí.</span><span class="sxs-lookup"><span data-stu-id="7de3b-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="7de3b-157">V následujícím příkladu je proměnná `target` místní pro `makeTheGame`, metoda, ve které je definován výraz lambda `playTheGame`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="7de3b-158">Všimněte si, že vrácený výraz lambda přiřazený `takeAGuess` v `Main`má stále přístup k místní proměnné `target`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="7de3b-159">Následující příklad ukazuje široké spektrum přístupových práv vnořeného výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="7de3b-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="7de3b-160">Když je vrácený výraz lambda proveden z `Main` jako `aDel`, přistupuje k těmto prvkům:</span><span class="sxs-lookup"><span data-stu-id="7de3b-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="7de3b-161">Pole třídy, ve které je definováno: `aField`</span><span class="sxs-lookup"><span data-stu-id="7de3b-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="7de3b-162">Vlastnost třídy, ve které je definována: `aProp`</span><span class="sxs-lookup"><span data-stu-id="7de3b-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="7de3b-163">Parametr metody `functionWithNestedLambda`, ve kterém je definován: `level1`</span><span class="sxs-lookup"><span data-stu-id="7de3b-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="7de3b-164">Místní proměnná `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="7de3b-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="7de3b-165">Parametr výrazu lambda, ve kterém je vnořený: `level2`</span><span class="sxs-lookup"><span data-stu-id="7de3b-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="7de3b-166">Převod na typ delegáta</span><span class="sxs-lookup"><span data-stu-id="7de3b-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="7de3b-167">Výraz lambda lze implicitně převést na kompatibilní typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="7de3b-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="7de3b-168">Informace o obecných požadavcích na kompatibilitu naleznete v tématu [odlehčený převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="7de3b-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="7de3b-169">Například následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající signaturu delegáta.</span><span class="sxs-lookup"><span data-stu-id="7de3b-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="7de3b-170">Následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající signaturu delegáta.</span><span class="sxs-lookup"><span data-stu-id="7de3b-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="7de3b-171">Pokud přiřadíte výrazy lambda delegátům nebo je předáte jako argumenty procedurám, můžete zadat názvy parametrů, ale vynechat jejich datové typy, aby bylo možné typy přenášet z delegáta.</span><span class="sxs-lookup"><span data-stu-id="7de3b-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="7de3b-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="7de3b-172">Examples</span></span>

- <span data-ttu-id="7de3b-173">Následující příklad definuje výraz lambda, který vrací `True`, pokud má argument null přiřazenou hodnotu a `False`, pokud je jeho hodnota `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7de3b-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="7de3b-174">Následující příklad definuje výraz lambda, který vrátí index posledního prvku v poli.</span><span class="sxs-lookup"><span data-stu-id="7de3b-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="7de3b-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7de3b-175">See also</span></span>

- [<span data-ttu-id="7de3b-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="7de3b-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7de3b-177">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7de3b-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7de3b-178">Delegáti</span><span class="sxs-lookup"><span data-stu-id="7de3b-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="7de3b-179">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="7de3b-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="7de3b-180">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="7de3b-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="7de3b-181">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="7de3b-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="7de3b-182">Postupy: Předání procedur jinému postupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7de3b-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="7de3b-183">Postupy: Vytvoření výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="7de3b-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="7de3b-184">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="7de3b-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
