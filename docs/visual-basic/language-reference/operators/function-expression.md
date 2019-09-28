---
title: Function – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 0ab4a77395b478df06f34240212438f3e6e18f6e
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592209"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="adb40-102">Function – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="adb40-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="adb40-103">Deklaruje parametry a kód, které definují výraz lambda funkce.</span><span class="sxs-lookup"><span data-stu-id="adb40-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adb40-104">Syntax</span></span>  
  
```vb  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="adb40-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="adb40-105">Parts</span></span>  
  
|<span data-ttu-id="adb40-106">Termín</span><span class="sxs-lookup"><span data-stu-id="adb40-106">Term</span></span>|<span data-ttu-id="adb40-107">Definice</span><span class="sxs-lookup"><span data-stu-id="adb40-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="adb40-108">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="adb40-108">Optional.</span></span> <span data-ttu-id="adb40-109">Seznam místních názvů proměnných, které reprezentují parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="adb40-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="adb40-110">Závorky musí být přítomny i v případě, že je seznam prázdný.</span><span class="sxs-lookup"><span data-stu-id="adb40-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="adb40-111">Viz [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="adb40-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="adb40-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="adb40-112">Required.</span></span> <span data-ttu-id="adb40-113">Jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="adb40-113">A single expression.</span></span> <span data-ttu-id="adb40-114">Typ výrazu je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="adb40-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="adb40-115">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="adb40-115">Required.</span></span> <span data-ttu-id="adb40-116">Seznam příkazů, které vrací hodnotu pomocí příkazu `Return`.</span><span class="sxs-lookup"><span data-stu-id="adb40-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="adb40-117">(Viz [návratový příkaz](../../../visual-basic/language-reference/statements/return-statement.md).) Typ vrácené hodnoty je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="adb40-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adb40-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adb40-118">Remarks</span></span>  
 <span data-ttu-id="adb40-119">*Výraz lambda* je funkce bez názvu, který počítá a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="adb40-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="adb40-120">Výraz lambda můžete použít kdekoli, kde můžete použít typ delegáta, s výjimkou argumentu pro `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="adb40-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="adb40-121">Další informace o delegátech a použití výrazů lambda s delegáty naleznete v tématu [příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) a [odlehčený převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="adb40-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="adb40-122">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="adb40-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="adb40-123">Syntaxe výrazu lambda se podobá funkci standardní funkce.</span><span class="sxs-lookup"><span data-stu-id="adb40-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="adb40-124">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="adb40-124">The differences are as follows:</span></span>  
  
- <span data-ttu-id="adb40-125">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="adb40-125">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="adb40-126">Výrazy lambda nemůžou mít modifikátory, například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="adb40-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="adb40-127">Výrazy lambda nepoužívají klauzuli `As` k určení návratového typu funkce.</span><span class="sxs-lookup"><span data-stu-id="adb40-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="adb40-128">Místo toho je typ odvozen z hodnoty, na kterou se tělo jednořádkového výrazu lambda vyhodnocuje, nebo návratovou hodnotu víceřádkového výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="adb40-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="adb40-129">Například pokud tělo jednořádkového výrazu lambda je `Where cust.City = "London"`, jeho návratový typ je `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="adb40-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="adb40-130">Tělo výrazu lambda s jedním řádkem musí být výraz, nikoli příkaz.</span><span class="sxs-lookup"><span data-stu-id="adb40-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="adb40-131">Tělo může být tvořeno voláním procedury funkce, ale nikoli voláním procedury Sub.</span><span class="sxs-lookup"><span data-stu-id="adb40-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
- <span data-ttu-id="adb40-132">Buď musí mít všechny parametry zadané datové typy, nebo musí být všechny odvoditelné.</span><span class="sxs-lookup"><span data-stu-id="adb40-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="adb40-133">Nepovinné parametry a parametry ParamArray nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="adb40-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
- <span data-ttu-id="adb40-134">Obecné parametry nejsou povolené.</span><span class="sxs-lookup"><span data-stu-id="adb40-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="adb40-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="adb40-135">Example</span></span>  
 <span data-ttu-id="adb40-136">Následující příklady znázorňují dva způsoby, jak vytvořit jednoduché výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="adb40-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="adb40-137">První používá `Dim` k poskytnutí názvu funkce.</span><span class="sxs-lookup"><span data-stu-id="adb40-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="adb40-138">Chcete-li zavolat funkci, odešlete hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="adb40-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="adb40-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="adb40-139">Example</span></span>  
 <span data-ttu-id="adb40-140">Alternativně můžete deklarovat a spustit funkci ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="adb40-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="adb40-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="adb40-141">Example</span></span>  
 <span data-ttu-id="adb40-142">Následuje příklad výrazu lambda, který zvyšuje svůj argument a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="adb40-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="adb40-143">V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro funkci.</span><span class="sxs-lookup"><span data-stu-id="adb40-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="adb40-144">Další příklady naleznete v tématu [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="adb40-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="adb40-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="adb40-145">Example</span></span>  
 <span data-ttu-id="adb40-146">Lambda výrazy tvoří mnoho operátorů dotazu v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] a lze je použít explicitně v dotazech založených na metodách.</span><span class="sxs-lookup"><span data-stu-id="adb40-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="adb40-147">Následující příklad ukazuje typický dotaz [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] následovaný překladem dotazu do formátu metody.</span><span class="sxs-lookup"><span data-stu-id="adb40-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="adb40-148">Další informace o metodách dotazů naleznete v tématu [dotazy](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="adb40-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="adb40-149">Další informace o standardních operátorech dotazu najdete v tématu [Přehled standardních operátorů dotazů](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="adb40-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb40-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adb40-150">See also</span></span>

- [<span data-ttu-id="adb40-151">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="adb40-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="adb40-152">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="adb40-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="adb40-153">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="adb40-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="adb40-154">Příkazy</span><span class="sxs-lookup"><span data-stu-id="adb40-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="adb40-155">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="adb40-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [<span data-ttu-id="adb40-156">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="adb40-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [<span data-ttu-id="adb40-157">Operátor If</span><span class="sxs-lookup"><span data-stu-id="adb40-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="adb40-158">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="adb40-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
