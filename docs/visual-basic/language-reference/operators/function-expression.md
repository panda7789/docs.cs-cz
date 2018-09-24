---
title: Function – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: cfdd17f6f4ee6c4ddb3fa73ab3ec9c5ce46a162f
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46702995"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="748b7-102">Function – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="748b7-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="748b7-103">Deklaruje parametry a kód, které definují výraz lambda funkce.</span><span class="sxs-lookup"><span data-stu-id="748b7-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="748b7-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="748b7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="748b7-105">Parts</span></span>  
  
|<span data-ttu-id="748b7-106">Termín</span><span class="sxs-lookup"><span data-stu-id="748b7-106">Term</span></span>|<span data-ttu-id="748b7-107">Definice</span><span class="sxs-lookup"><span data-stu-id="748b7-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="748b7-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="748b7-108">Optional.</span></span> <span data-ttu-id="748b7-109">Seznam místní názvy proměnných, které představují parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="748b7-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="748b7-110">Závorky musí být k dispozici i v případě, že je seznam prázdný.</span><span class="sxs-lookup"><span data-stu-id="748b7-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="748b7-111">Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="748b7-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="748b7-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="748b7-112">Required.</span></span> <span data-ttu-id="748b7-113">Jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="748b7-113">A single expression.</span></span> <span data-ttu-id="748b7-114">Typ výrazu je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="748b7-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="748b7-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="748b7-115">Required.</span></span> <span data-ttu-id="748b7-116">Seznam příkazů, který vrací hodnotu s použitím `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="748b7-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="748b7-117">(Viz [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).) Typ hodnoty vrácené je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="748b7-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="748b7-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="748b7-118">Remarks</span></span>  
 <span data-ttu-id="748b7-119">A *výraz lambda* je funkce bez názvu, který vypočítává a vrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="748b7-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="748b7-120">Výraz lambda můžete použít kdekoli můžete použít typ delegáta, s výjimkou jako argument `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="748b7-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="748b7-121">Další informace o delegátech a použití výrazů lambda s delegáty, naleznete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="748b7-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="748b7-122">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="748b7-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="748b7-123">Syntaxe výrazu lambda se podobá u standardní funkci.</span><span class="sxs-lookup"><span data-stu-id="748b7-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="748b7-124">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="748b7-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="748b7-125">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="748b7-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="748b7-126">Výrazy lambda nemůžou mít modifikátory, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="748b7-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="748b7-127">Výrazy lambda se nepoužívá `As` klauzule k určení návratového typu funkce.</span><span class="sxs-lookup"><span data-stu-id="748b7-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="748b7-128">Místo toho typ je odvozen z hodnotu, která se vyhodnotí jako hlavní část výrazu lambda jednořádkového nebo návratovou hodnotu víceřádkového výrazu lambda výrazu.</span><span class="sxs-lookup"><span data-stu-id="748b7-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="748b7-129">Například, pokud je hlavní část výrazu lambda jednořádkového `Where cust.City = "London"`, je její typ vrácené hodnoty `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="748b7-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="748b7-130">Výraz, ne příkaz musí být tělo tohoto výrazu lambda jednořádkového.</span><span class="sxs-lookup"><span data-stu-id="748b7-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="748b7-131">Text se může skládat z volání proceduru function, ale ne voláním procedury sub.</span><span class="sxs-lookup"><span data-stu-id="748b7-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="748b7-132">Buď všechny parametry musí mít zadaný datové typy nebo všechny musí být odvozený.</span><span class="sxs-lookup"><span data-stu-id="748b7-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="748b7-133">Volitelné a Paramarray parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="748b7-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="748b7-134">Obecné parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="748b7-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="748b7-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="748b7-135">Example</span></span>  
 <span data-ttu-id="748b7-136">Následující příklady ukazují dva způsoby, jak vytvořit jednoduchý lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="748b7-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="748b7-137">První použití `Dim` k poskytnutí názvu pro funkci.</span><span class="sxs-lookup"><span data-stu-id="748b7-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="748b7-138">Pro volání funkce, předáte hodnotu parametru.</span><span class="sxs-lookup"><span data-stu-id="748b7-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="748b7-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="748b7-139">Example</span></span>  
 <span data-ttu-id="748b7-140">Můžete také deklarovat a spustit funkci ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="748b7-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="748b7-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="748b7-141">Example</span></span>  
 <span data-ttu-id="748b7-142">Tady je příklad výraz lambda, který zvýší její argument a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="748b7-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="748b7-143">Příklad ukazuje obě jedním řádkem a víceřádkového výrazu lambda syntaxe výrazu pro funkci.</span><span class="sxs-lookup"><span data-stu-id="748b7-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="748b7-144">Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="748b7-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="748b7-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="748b7-145">Example</span></span>  
 <span data-ttu-id="748b7-146">Výrazy lambda tvoří základ mnoho operátorů dotazu v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]a můžete explicitně použít v dotazech založených na volání metody.</span><span class="sxs-lookup"><span data-stu-id="748b7-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="748b7-147">Následující příklad ukazuje typickou [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, za nímž následuje překladu dotazu do formátu metody.</span><span class="sxs-lookup"><span data-stu-id="748b7-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="748b7-148">Další informace o metodách dotazu naleznete v tématu [dotazy](../../../visual-basic/language-reference/queries/index.md).</span><span class="sxs-lookup"><span data-stu-id="748b7-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/index.md).</span></span> <span data-ttu-id="748b7-149">Další informace o standardních operátorů pro dotazování, naleznete v tématu [přehled standardních operátorů dotazu](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="748b7-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748b7-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="748b7-150">See Also</span></span>  
 [<span data-ttu-id="748b7-151">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="748b7-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="748b7-152">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="748b7-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="748b7-153">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="748b7-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="748b7-154">Příkazy</span><span class="sxs-lookup"><span data-stu-id="748b7-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="748b7-155">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="748b7-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="748b7-156">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="748b7-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="748b7-157">Operátor If</span><span class="sxs-lookup"><span data-stu-id="748b7-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="748b7-158">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="748b7-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
