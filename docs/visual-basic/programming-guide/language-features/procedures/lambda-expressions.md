---
title: Výrazy Lambda (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c45500dc7a1e59a7ac83d43b826ca4cbfca6efb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654791"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="526e5-102">Výrazy Lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="526e5-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="526e5-103">A *výrazu lambda* je funkce nebo podprogramu bez názvu, který lze použít bez ohledu na delegáta je platný.</span><span class="sxs-lookup"><span data-stu-id="526e5-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="526e5-104">Výrazy lambda může být funkce nebo subrutiny a může být jeden nebo více řádků.</span><span class="sxs-lookup"><span data-stu-id="526e5-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="526e5-105">Můžete předat hodnoty z aktuálního oboru do výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="526e5-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="526e5-106">`RemoveHandler` Příkaz je výjimku.</span><span class="sxs-lookup"><span data-stu-id="526e5-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="526e5-107">Nelze předat výrazu lambda v pro parametr delegáta `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="526e5-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="526e5-108">Lambda – výrazy vytvoříte pomocí `Function` nebo `Sub` – klíčové slovo, stejně jako můžete vytvořit standardní funkce nebo podprogramu.</span><span class="sxs-lookup"><span data-stu-id="526e5-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="526e5-109">Lambda – výrazy jsou však součástí příkazu.</span><span class="sxs-lookup"><span data-stu-id="526e5-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="526e5-110">V následujícím příkladu je výraz lambda, který zvýší jeho argumentů a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="526e5-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="526e5-111">Příklad ukazuje, jak jednom řádku a víceřádkový syntaxe výrazu lambda pro funkci.</span><span class="sxs-lookup"><span data-stu-id="526e5-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]  
  
 <span data-ttu-id="526e5-112">V následujícím příkladu je výraz lambda, která hodnotu zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="526e5-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="526e5-113">Příklad ukazuje, jak jednom řádku a víceřádkový syntaxe výrazu lambda pro podprogramu.</span><span class="sxs-lookup"><span data-stu-id="526e5-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]  
  
 <span data-ttu-id="526e5-114">Všimněte si, že v předchozích příkladech jsou výrazy lambda přiřazené k název proměnné.</span><span class="sxs-lookup"><span data-stu-id="526e5-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="526e5-115">Vždy, když odkazujete na proměnnou, můžete vyvolat výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="526e5-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="526e5-116">Můžete také deklarovat a vyvolání výrazu lambda ve stejnou dobu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="526e5-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]  
  
 <span data-ttu-id="526e5-117">Výraz lambda může být vrácen jako hodnota z volání funkce (jak je znázorněno v příkladu v [kontextu](#context) později v tomto tématu), nebo předaná jako argument parametr, který přebírá typem delegáta, jak je znázorněno v následující Příklad.</span><span class="sxs-lookup"><span data-stu-id="526e5-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="526e5-118">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="526e5-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="526e5-119">Syntaxe výrazu lambda podobá se standardní funkce nebo podprogramu.</span><span class="sxs-lookup"><span data-stu-id="526e5-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="526e5-120">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="526e5-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="526e5-121">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="526e5-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="526e5-122">Lambda – výrazy nemůže mít modifikátory, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="526e5-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="526e5-123">Jeden řádek lambda funkce nepoužívají `As` klauzule k určení návratový typ.</span><span class="sxs-lookup"><span data-stu-id="526e5-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="526e5-124">Místo toho je typ odvodit z hodnotu, která vyhodnotí jako text výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="526e5-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="526e5-125">Například, pokud je text výrazu lambda `cust.City = "London"`, je její návratový typ `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="526e5-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="526e5-126">V Víceřádkový lambda funkce, můžete buď zadat návratový typ pomocí `As` klauzuli, nebo vynechejte `As` klauzule tak, že je návratový typ odvodit.</span><span class="sxs-lookup"><span data-stu-id="526e5-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="526e5-127">Když `As` klauzule je zadán pro funkci Víceřádkový lambda, je jako typ dominantní ze všech odvodit návratový typ `Return` příkazy ve funkci Víceřádkový lambda.</span><span class="sxs-lookup"><span data-stu-id="526e5-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="526e5-128">*Dominantní typ* je jedinečný typ, který všechny ostatní typy můžete rozšířit do.</span><span class="sxs-lookup"><span data-stu-id="526e5-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="526e5-129">Pokud tento typ jedinečného nelze určit, dominantní typ je jedinečný typ, který k můžete zúžit všechny ostatní typy v poli.</span><span class="sxs-lookup"><span data-stu-id="526e5-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="526e5-130">Pokud žádná z těchto jedinečný se dá určit, že dominantní typ je `Object`.</span><span class="sxs-lookup"><span data-stu-id="526e5-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="526e5-131">V takovém případě pokud `Option Strict` je nastaven na `On`, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="526e5-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="526e5-132">Například, pokud zadané výrazy `Return` příkaz obsahovat hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="526e5-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="526e5-133">Obě `Integer` a `Long` rozšíří do `Double` pouze a `Double`.</span><span class="sxs-lookup"><span data-stu-id="526e5-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="526e5-134">Proto `Double` dominantní typu.</span><span class="sxs-lookup"><span data-stu-id="526e5-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="526e5-135">Další informace najdete v tématu [Widening a zužující převody](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="526e5-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="526e5-136">Tělo funkce jeden řádek musí být výraz, který vrátí hodnotu, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="526e5-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="526e5-137">Neexistuje žádné `Return` údajů pro funkce jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="526e5-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="526e5-138">Hodnota vrácená funkcí jeden řádek je hodnota výrazu v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="526e5-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="526e5-139">Tělo podprogramu jeden řádek musí být příkaz jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="526e5-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="526e5-140">Jeden řádek funkce a subrutiny nezahrnují `End Function` nebo `End Sub` příkaz.</span><span class="sxs-lookup"><span data-stu-id="526e5-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="526e5-141">Datový typ parametru výrazu lambda můžete zadat pomocí `As` lze odvodit – klíčové slovo nebo datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="526e5-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="526e5-142">Buď všechny parametry musí mít zadán odvodit datové typy nebo všechny.</span><span class="sxs-lookup"><span data-stu-id="526e5-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="526e5-143">`Optional` a `Paramarray` parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="526e5-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="526e5-144">Obecné parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="526e5-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="526e5-145">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="526e5-145">Async Lambdas</span></span>  
 <span data-ttu-id="526e5-146">Můžete snadno vytvořit lambda – výrazy a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) a [Await – operátor](../../../../visual-basic/language-reference/operators/await-operator.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="526e5-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="526e5-147">Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a čeká použití asynchronní metody `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="526e5-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="526e5-148">Stejné obslužné rutiny události můžete přidat pomocí asynchronní lambda v [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="526e5-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="526e5-149">Chcete-li přidat Tato obslužná rutina, přidejte `Async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="526e5-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="526e5-150">Další informace o tom, jak vytvořit a použít asynchronní metody najdete v tématu [asynchronní programování s Async a Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="526e5-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <a name="context"></a> <span data-ttu-id="526e5-151">Kontext</span><span class="sxs-lookup"><span data-stu-id="526e5-151">Context</span></span>  
 <span data-ttu-id="526e5-152">Výraz lambda sdílí jeho kontext k oboru, ve kterém je definovaný.</span><span class="sxs-lookup"><span data-stu-id="526e5-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="526e5-153">Má stejné oprávnění jako jakékoli kód napsaný v oboru obsahujícího.</span><span class="sxs-lookup"><span data-stu-id="526e5-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="526e5-154">Poskytuje přístup k členské proměnné, funkce a předplatných, `Me`a parametry a místní proměnné v oboru obsahujícího.</span><span class="sxs-lookup"><span data-stu-id="526e5-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="526e5-155">Přístup k místní proměnné a parametry v oboru obsahujícího můžete rozšířit nad rámec doba platnosti tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="526e5-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="526e5-156">Dokud není k dispozici pro uvolňování paměti s delegátem, která odkazuje na výraz lambda, přístup k proměnným v původní prostředí se zachová.</span><span class="sxs-lookup"><span data-stu-id="526e5-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="526e5-157">V následujícím příkladu, proměnné `target` je místní pro `makeTheGame`, metoda, ve kterém výrazu lambda `playTheGame` je definována.</span><span class="sxs-lookup"><span data-stu-id="526e5-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="526e5-158">Všimněte si, že výraz lambda vrácený přiřazené `takeAGuess` v `Main`, stále má přístup k místní proměnné `target`.</span><span class="sxs-lookup"><span data-stu-id="526e5-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]  
  
 <span data-ttu-id="526e5-159">Následující příklad ukazuje širokou škálu přístupová práva výrazu vnořené lambda.</span><span class="sxs-lookup"><span data-stu-id="526e5-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="526e5-160">Provedení výrazu lambda vrácená z `Main` jako `aDel`, přistupuje k tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="526e5-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="526e5-161">Pole třídy, ve kterém je definovaný: `aField`</span><span class="sxs-lookup"><span data-stu-id="526e5-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="526e5-162">Vlastnosti třídy, ve kterém je definovaný: `aProp`</span><span class="sxs-lookup"><span data-stu-id="526e5-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="526e5-163">Parametr metody `functionWithNestedLambda`, ve kterém je definována: `level1`</span><span class="sxs-lookup"><span data-stu-id="526e5-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="526e5-164">Místní proměnná `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="526e5-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="526e5-165">Parametr výrazu lambda, ve kterém jsou vnořeny: `level2`</span><span class="sxs-lookup"><span data-stu-id="526e5-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="526e5-166">Převádění na typ delegáta</span><span class="sxs-lookup"><span data-stu-id="526e5-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="526e5-167">Výraz lambda může implicitně převést na typ kompatibilní delegáta.</span><span class="sxs-lookup"><span data-stu-id="526e5-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="526e5-168">Informace o obecné požadavky na kompatibilitu najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="526e5-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="526e5-169">Například následující příklad kódu ukazuje výrazu lambda, která se implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající podpisu delegáta.</span><span class="sxs-lookup"><span data-stu-id="526e5-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]  
  
 <span data-ttu-id="526e5-170">Následující příklad kódu ukazuje výrazu lambda, která se implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající podpisu delegáta.</span><span class="sxs-lookup"><span data-stu-id="526e5-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]  
  
 <span data-ttu-id="526e5-171">Když výrazy lambda přiřadit delegáty nebo je předat jako argumenty procedury, můžete zadat názvy parametrů, ale vynechejte jejich datové typy, když necháte typy provedou z delegáta.</span><span class="sxs-lookup"><span data-stu-id="526e5-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="526e5-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="526e5-172">Examples</span></span>  
  
-   <span data-ttu-id="526e5-173">V následujícím příkladu definuje výraz lambda, který vrací `True` Pokud má argument s možnou hodnotou Null přiřazenou hodnotu, a `False` Pokud je jeho hodnota `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="526e5-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]  
  
-   <span data-ttu-id="526e5-174">V následujícím příkladu definuje výraz lambda, který vrátí index posledním elementem pole.</span><span class="sxs-lookup"><span data-stu-id="526e5-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="526e5-175">Viz také</span><span class="sxs-lookup"><span data-stu-id="526e5-175">See Also</span></span>  
 [<span data-ttu-id="526e5-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="526e5-176">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="526e5-177">Úvod do LINQ v jazyku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="526e5-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="526e5-178">Delegáti</span><span class="sxs-lookup"><span data-stu-id="526e5-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="526e5-179">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="526e5-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="526e5-180">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="526e5-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="526e5-181">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="526e5-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [<span data-ttu-id="526e5-182">Postupy: předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="526e5-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="526e5-183">Postupy: Vytvoření výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="526e5-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)  
 [<span data-ttu-id="526e5-184">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="526e5-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
