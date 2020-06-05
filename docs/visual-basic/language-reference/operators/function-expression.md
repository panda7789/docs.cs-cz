---
title: Function – výraz
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: a9b621ff03f833fcf0f07f876fd864ee963bef75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371178"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="f7fa2-102">Function – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7fa2-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="f7fa2-103">Deklaruje parametry a kód, které definují výraz lambda funkce.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fa2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7fa2-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="f7fa2-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f7fa2-105">Parts</span></span>  
  
|<span data-ttu-id="f7fa2-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="f7fa2-106">Term</span></span>|<span data-ttu-id="f7fa2-107">Definice</span><span class="sxs-lookup"><span data-stu-id="f7fa2-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="f7fa2-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-108">Optional.</span></span> <span data-ttu-id="f7fa2-109">Seznam místních názvů proměnných, které reprezentují parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="f7fa2-110">Závorky musí být přítomny i v případě, že je seznam prázdný.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="f7fa2-111">Viz [seznam parametrů](../statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa2-111">See [Parameter List](../statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="f7fa2-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-112">Required.</span></span> <span data-ttu-id="f7fa2-113">Jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-113">A single expression.</span></span> <span data-ttu-id="f7fa2-114">Typ výrazu je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="f7fa2-115">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-115">Required.</span></span> <span data-ttu-id="f7fa2-116">Seznam příkazů, které vrací hodnotu pomocí `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="f7fa2-117">(Viz [návratový příkaz](../statements/return-statement.md).) Typ vrácené hodnoty je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-117">(See [Return Statement](../statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7fa2-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7fa2-118">Remarks</span></span>  
 <span data-ttu-id="f7fa2-119">*Výraz lambda* je funkce bez názvu, který počítá a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="f7fa2-120">Můžete použít výraz lambda kdekoli, kde můžete použít typ delegáta, s výjimkou argumentu pro `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="f7fa2-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="f7fa2-121">Další informace o delegátech a použití výrazů lambda s delegáty naleznete v tématu [příkaz Delegate](../statements/delegate-statement.md) a [odlehčený převod delegáta](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa2-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="f7fa2-122">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="f7fa2-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="f7fa2-123">Syntaxe výrazu lambda se podobá funkci standardní funkce.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="f7fa2-124">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f7fa2-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="f7fa2-125">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="f7fa2-126">Výrazy lambda nemůžou mít modifikátory, například `Overloads` nebo `Overrides` .</span><span class="sxs-lookup"><span data-stu-id="f7fa2-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="f7fa2-127">Výrazy lambda nepoužívají `As` klauzuli k určení návratového typu funkce.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="f7fa2-128">Místo toho je typ odvozen z hodnoty, na kterou se tělo jednořádkového výrazu lambda vyhodnocuje, nebo návratovou hodnotu víceřádkového výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="f7fa2-129">Například pokud tělo víceřádkového výrazu lambda je `Where cust.City = "London"` , jeho návratový typ je `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f7fa2-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="f7fa2-130">Tělo výrazu lambda s jedním řádkem musí být výraz, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="f7fa2-131">Tělo může být tvořeno voláním procedury funkce, ale nikoli voláním procedury Sub.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="f7fa2-132">Buď musí mít všechny parametry zadané datové typy, nebo musí být všechny odvoditelné.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="f7fa2-133">Nepovinné parametry a parametry ParamArray nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="f7fa2-134">Obecné parametry nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7fa2-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7fa2-135">Example</span></span>  
 <span data-ttu-id="f7fa2-136">Následující příklady znázorňují dva způsoby, jak vytvořit jednoduché výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="f7fa2-137">První používá `Dim` k zadání názvu funkce.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="f7fa2-138">Chcete-li zavolat funkci, odešlete hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="f7fa2-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7fa2-139">Example</span></span>  
 <span data-ttu-id="f7fa2-140">Alternativně můžete deklarovat a spustit funkci ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="f7fa2-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7fa2-141">Example</span></span>  
 <span data-ttu-id="f7fa2-142">Následuje příklad výrazu lambda, který zvyšuje svůj argument a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="f7fa2-143">V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro funkci.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="f7fa2-144">Další příklady naleznete v tématu [lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa2-144">For more examples, see [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="f7fa2-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7fa2-145">Example</span></span>  
 <span data-ttu-id="f7fa2-146">Výrazy lambda jsou základem mnoha operátorů dotazu v jazyce LINQ (Language-Integrated Query) a lze je použít explicitně v dotazech založených na metodách.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-146">Lambda expressions underlie many of the query operators in Language-Integrated Query (LINQ), and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="f7fa2-147">Následující příklad ukazuje typický dotaz LINQ následovaný překladem dotazu do formátu metody.</span><span class="sxs-lookup"><span data-stu-id="f7fa2-147">The following example shows a typical LINQ query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="f7fa2-148">Další informace o metodách dotazů naleznete v tématu [dotazy](../queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa2-148">For more information about query methods, see [Queries](../queries/index.md).</span></span> <span data-ttu-id="f7fa2-149">Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorů dotazů](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa2-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7fa2-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7fa2-150">See also</span></span>

- [<span data-ttu-id="f7fa2-151">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="f7fa2-151">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="f7fa2-152">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="f7fa2-152">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="f7fa2-153">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="f7fa2-153">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="f7fa2-154">Příkazy</span><span class="sxs-lookup"><span data-stu-id="f7fa2-154">Statements</span></span>](../../programming-guide/language-features/statements.md)
- [<span data-ttu-id="f7fa2-155">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="f7fa2-155">Value Comparisons</span></span>](../../programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="f7fa2-156">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="f7fa2-156">Boolean Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="f7fa2-157">If – operátor</span><span class="sxs-lookup"><span data-stu-id="f7fa2-157">If Operator</span></span>](if-operator.md)
- [<span data-ttu-id="f7fa2-158">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="f7fa2-158">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
