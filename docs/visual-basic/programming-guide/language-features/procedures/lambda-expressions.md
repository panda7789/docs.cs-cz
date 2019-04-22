---
title: Lambda – výrazy (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: c43739e098a91d54d300fa7074d1563da179c0e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832109"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="d273d-102">Lambda – výrazy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d273d-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="d273d-103">A *výraz lambda* je funkce nebo podprogramu bez názvu, který lze použít bez ohledu na to delegát je platný.</span><span class="sxs-lookup"><span data-stu-id="d273d-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="d273d-104">Výrazy lambda může být funkce nebo podprogramy a může být jeden nebo více řádků.</span><span class="sxs-lookup"><span data-stu-id="d273d-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="d273d-105">Můžete předat hodnoty z aktuálního oboru pro výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="d273d-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d273d-106">`RemoveHandler` Příkaz je výjimku.</span><span class="sxs-lookup"><span data-stu-id="d273d-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="d273d-107">Nelze předat výraz lambda v parametru delegáta `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="d273d-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="d273d-108">Vytvoříte pomocí výrazů lambda `Function` nebo `Sub` – klíčové slovo, podobně jako můžete vytvořit standardní funkce nebo podprogramu.</span><span class="sxs-lookup"><span data-stu-id="d273d-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="d273d-109">Výrazy lambda jsou však zahrnuty v příkazu.</span><span class="sxs-lookup"><span data-stu-id="d273d-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="d273d-110">V následujícím příkladu je výraz lambda, který zvýší její argument a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d273d-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="d273d-111">Příklad ukazuje obě lambda jednořádkového a více řádky syntaxe výrazu pro funkci.</span><span class="sxs-lookup"><span data-stu-id="d273d-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 <span data-ttu-id="d273d-112">V následujícím příkladu je výraz lambda, který zapíše hodnoty do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d273d-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="d273d-113">Příklad ukazuje obě jedním řádkem a víceřádkového výrazu lambda výraz syntaxe podprogram.</span><span class="sxs-lookup"><span data-stu-id="d273d-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 <span data-ttu-id="d273d-114">Všimněte si, že v předchozích příkladech jsou lambda výrazy přiřazeny k názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="d273d-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="d273d-115">Pokaždé, když odkazujete na proměnnou, vyvolání lambda výrazu.</span><span class="sxs-lookup"><span data-stu-id="d273d-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="d273d-116">Můžete také deklarovat a volat lambda výraz ve stejnou dobu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d273d-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 <span data-ttu-id="d273d-117">Výraz lambda může být vrácen jako hodnotu volání funkce (jak je znázorněno v příkladu [kontextu](#context) později v tomto tématu), nebo předaný jako argument pro parametr, který přijímá typ delegáta, jak je znázorněno v následujícím Příklad.</span><span class="sxs-lookup"><span data-stu-id="d273d-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="d273d-118">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="d273d-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="d273d-119">Syntaxe výrazu lambda se podobá standardní funkce nebo podprogram.</span><span class="sxs-lookup"><span data-stu-id="d273d-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="d273d-120">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="d273d-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="d273d-121">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="d273d-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="d273d-122">Výrazy lambda nemůžou mít modifikátory, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="d273d-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="d273d-123">Funkce lambda jednořádkového nepoužívejte `As` klauzule k určení návratového typu.</span><span class="sxs-lookup"><span data-stu-id="d273d-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="d273d-124">Místo toho typ je odvozen z hodnotu, která se vyhodnotí jako hlavní část výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="d273d-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="d273d-125">Například pokud tělo výrazu lambda je `cust.City = "London"`, je její typ vrácené hodnoty `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d273d-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="d273d-126">Ve funkcích víceřádkového výrazu lambda, můžete zadat typ vrácené hodnoty pomocí `As` klauzuli, nebo vynechejte `As` klauzule tak, aby návratový typ je odvozen.</span><span class="sxs-lookup"><span data-stu-id="d273d-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="d273d-127">Když `As` klauzule vynecháte víceřádkového výrazu lambda funkce, návratový typ je odvozen dominantní typ ze všech `Return` příkazy ve funkci víceřádkového výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="d273d-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="d273d-128">*Dominantní typ* je jedinečný typ, který lze rozšířit všechny ostatní typy na.</span><span class="sxs-lookup"><span data-stu-id="d273d-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="d273d-129">Pokud nelze určit tento jedinečný typ, dominantní typ je jedinečný typ, který můžete zúžit všechny typy jako pole k.</span><span class="sxs-lookup"><span data-stu-id="d273d-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="d273d-130">Pokud ani jeden z těchto jedinečných typů nelze určit, dominantní typ je `Object`.</span><span class="sxs-lookup"><span data-stu-id="d273d-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="d273d-131">V takovém případě pokud `Option Strict` je nastavena na `On`, dojde k chybě kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d273d-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="d273d-132">Například, pokud zadaný výraz pro `Return` příkaz obsahovat hodnoty typu `Integer`, `Long`, a `Double`, výsledné pole je typu `Double`.</span><span class="sxs-lookup"><span data-stu-id="d273d-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="d273d-133">Obě `Integer` a `Long` rozšířit na `Double` a pouze `Double`.</span><span class="sxs-lookup"><span data-stu-id="d273d-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="d273d-134">Proto `Double` dominantní typ je.</span><span class="sxs-lookup"><span data-stu-id="d273d-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="d273d-135">Další informace najdete v tématu [Widening a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="d273d-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="d273d-136">Výraz, který vrací hodnotu, ne příkaz, musí být tělo funkce jedním řádkem.</span><span class="sxs-lookup"><span data-stu-id="d273d-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="d273d-137">Neexistuje žádná `Return` příkaz pro funkce jedním řádkem.</span><span class="sxs-lookup"><span data-stu-id="d273d-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="d273d-138">Hodnota vrácená funkcí jedním řádkem je hodnota výrazu v těle funkce.</span><span class="sxs-lookup"><span data-stu-id="d273d-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="d273d-139">Jednořádkového příkazu musí být tělo tohoto podprogram jedním řádkem.</span><span class="sxs-lookup"><span data-stu-id="d273d-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="d273d-140">Jedním řádkem funkce a podprogramy nezahrnují `End Function` nebo `End Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="d273d-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="d273d-141">Datový typ parametru výrazu lambda můžete určit pomocí `As` jde odvodit – klíčové slovo nebo datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="d273d-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="d273d-142">Buď všechny parametry musí mít zadaný datové typy nebo všechny musí být odvozený.</span><span class="sxs-lookup"><span data-stu-id="d273d-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="d273d-143">`Optional` a `Paramarray` parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="d273d-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="d273d-144">Obecné parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="d273d-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="d273d-145">Asynchronní lambdy</span><span class="sxs-lookup"><span data-stu-id="d273d-145">Async Lambdas</span></span>  
 <span data-ttu-id="d273d-146">Můžete snadno vytvořit výrazy lambda a příkazy, které zahrnují asynchronní zpracování pomocí [asynchronní](../../../../visual-basic/language-reference/modifiers/async.md) a [operátor Await](../../../../visual-basic/language-reference/operators/await-operator.md) klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="d273d-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="d273d-147">Například následující příklad Windows Forms obsahuje obslužnou rutinu události, která volá a očekává asynchronní metodu, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="d273d-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="d273d-148">Stejný ovladač událostí můžete přidat pomocí asynchronní lambdy v [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d273d-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="d273d-149">Chcete-li přidat tuto obslužnou rutinu, přidejte `Async` modifikátor před seznam parametrů lambda, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d273d-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="d273d-150">Další informace o tom, jak vytvořit a používat asynchronní metody, naleznete v tématu [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="d273d-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="context"></a> <span data-ttu-id="d273d-151">Kontext</span><span class="sxs-lookup"><span data-stu-id="d273d-151">Context</span></span>  
 <span data-ttu-id="d273d-152">Výraz lambda sdílí jeho kontextu oboru, ve kterém je definována.</span><span class="sxs-lookup"><span data-stu-id="d273d-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="d273d-153">Má stejná přístupová práva jako libovolný kód napsaný v rozsah.</span><span class="sxs-lookup"><span data-stu-id="d273d-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="d273d-154">Jedná se o přístup k proměnné členů, funkcí a typu Sub, `Me`a parametrů a lokálních proměnných v nadřazeného oboru.</span><span class="sxs-lookup"><span data-stu-id="d273d-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="d273d-155">Přístup k místní proměnné a parametry v rozsah můžete rozšířit nad rámec doby života tohoto oboru.</span><span class="sxs-lookup"><span data-stu-id="d273d-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="d273d-156">Dokud delegát, který odkazuje na výraz lambda není k dispozici pro uvolňování paměti, přístup k proměnným v původní prostředí se zachová.</span><span class="sxs-lookup"><span data-stu-id="d273d-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="d273d-157">V následujícím příkladu proměnná `target` je lokální vzhledem k `makeTheGame`, metody, ve které výraz lambda `playTheGame` je definována.</span><span class="sxs-lookup"><span data-stu-id="d273d-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="d273d-158">Všimněte si, že vrácený výraz lambda, přiřazená `takeAGuess` v `Main`, má stále přístup k místní proměnné `target`.</span><span class="sxs-lookup"><span data-stu-id="d273d-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 <span data-ttu-id="d273d-159">Následující příklad ukazuje širokou škálu přístupová práva vnořený výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="d273d-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="d273d-160">Při spouštění vrácený výraz lambda se z `Main` jako `aDel`, přistupuje k tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="d273d-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="d273d-161">Pole třídy, ve kterém je definována: `aField`</span><span class="sxs-lookup"><span data-stu-id="d273d-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="d273d-162">Vlastnost třídy, ve kterém je definována: `aProp`</span><span class="sxs-lookup"><span data-stu-id="d273d-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="d273d-163">Parametr metody `functionWithNestedLambda`, ve kterém je definována: `level1`</span><span class="sxs-lookup"><span data-stu-id="d273d-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="d273d-164">Místní proměnná `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="d273d-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="d273d-165">Parametr lambda výrazu, ve kterém je vnořená: `level2`</span><span class="sxs-lookup"><span data-stu-id="d273d-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="d273d-166">Převádění na typ delegáta</span><span class="sxs-lookup"><span data-stu-id="d273d-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="d273d-167">Výraz lambda lze implicitně převést na typ delegáta kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="d273d-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="d273d-168">Informace o požadavcích na obecné kompatibility najdete v tématu [volný převod delegáta](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="d273d-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="d273d-169">Například následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Func(Of Integer, Boolean)` nebo odpovídající signatura delegáta.</span><span class="sxs-lookup"><span data-stu-id="d273d-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 <span data-ttu-id="d273d-170">Následující příklad kódu ukazuje výraz lambda, který implicitně převede na `Sub(Of Double, String, Double)` nebo odpovídající signatura delegáta.</span><span class="sxs-lookup"><span data-stu-id="d273d-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 <span data-ttu-id="d273d-171">Při přiřazení výrazy lambda na delegáty nebo předávat jako argumenty na postupy, můžete zadat názvy parametrů, ale vynechejte jejich datové typy, kde typy vytvářena z delegáta.</span><span class="sxs-lookup"><span data-stu-id="d273d-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d273d-172">Příklady</span><span class="sxs-lookup"><span data-stu-id="d273d-172">Examples</span></span>  
  
-   <span data-ttu-id="d273d-173">Následující příklad definuje výraz lambda, který vrátí `True` Pokud s možnou hodnotou Null argument má přiřazenou hodnotu, a `False` pokud její hodnota je `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="d273d-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
-   <span data-ttu-id="d273d-174">Následující příklad definuje výraz lambda, který vrátí index posledního prvku v poli.</span><span class="sxs-lookup"><span data-stu-id="d273d-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="d273d-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d273d-175">See also</span></span>

- [<span data-ttu-id="d273d-176">Procedury</span><span class="sxs-lookup"><span data-stu-id="d273d-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="d273d-177">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d273d-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d273d-178">Delegáti</span><span class="sxs-lookup"><span data-stu-id="d273d-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="d273d-179">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="d273d-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="d273d-180">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="d273d-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="d273d-181">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="d273d-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="d273d-182">Postupy: Předání procedur jiné proceduře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d273d-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="d273d-183">Postupy: Vytvoření výrazu Lambda</span><span class="sxs-lookup"><span data-stu-id="d273d-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="d273d-184">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="d273d-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
