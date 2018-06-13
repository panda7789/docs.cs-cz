---
title: Function – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 29bf95a336b6f6ed5c9c310c9ea7575a91089361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604884"
---
# <a name="function-expression-visual-basic"></a><span data-ttu-id="e1bf5-102">Function – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1bf5-102">Function Expression (Visual Basic)</span></span>
<span data-ttu-id="e1bf5-103">Deklaruje, parametry a kód, který definovat výraz lambda funkce.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-103">Declares the parameters and code that define a function lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1bf5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1bf5-104">Syntax</span></span>  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="e1bf5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e1bf5-105">Parts</span></span>  
  
|<span data-ttu-id="e1bf5-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e1bf5-106">Term</span></span>|<span data-ttu-id="e1bf5-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e1bf5-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="e1bf5-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-108">Optional.</span></span> <span data-ttu-id="e1bf5-109">Seznam místní názvy proměnných, které představují parametry tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-109">A list of local variable names that represent the parameters of this procedure.</span></span> <span data-ttu-id="e1bf5-110">Závorkách musí být k dispozici i v případě, že seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="e1bf5-111">V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="e1bf5-111">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`expression`|<span data-ttu-id="e1bf5-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-112">Required.</span></span> <span data-ttu-id="e1bf5-113">Jeden výraz.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-113">A single expression.</span></span> <span data-ttu-id="e1bf5-114">Typ výrazu je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-114">The type of the expression is the return type of the function.</span></span>|  
|`statements`|<span data-ttu-id="e1bf5-115">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-115">Required.</span></span> <span data-ttu-id="e1bf5-116">Seznam příkazů, která vrátí hodnotu pomocí `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-116">A list of statements that returns a value by using the `Return` statement.</span></span> <span data-ttu-id="e1bf5-117">(Viz [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).) Typ hodnoty vrácené je návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-117">(See [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).) The type of the value returned is the return type of the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1bf5-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1bf5-118">Remarks</span></span>  
 <span data-ttu-id="e1bf5-119">A *výrazu lambda* je funkce, bez název, který vypočítá a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-119">A *lambda expression* is a function without a name that calculates and returns a value.</span></span> <span data-ttu-id="e1bf5-120">Výraz lambda lze použít kdekoli můžete použít typem delegáta, s výjimkou jako argument pro `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-120">You can use a lambda expression anywhere you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="e1bf5-121">Další informace o Delegáti a použití výrazů lambda s delegáti najdete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="e1bf5-121">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="e1bf5-122">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="e1bf5-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="e1bf5-123">Syntaxe výrazu lambda podobá se standardní funkce.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-123">The syntax of a lambda expression resembles that of a standard function.</span></span> <span data-ttu-id="e1bf5-124">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e1bf5-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="e1bf5-125">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="e1bf5-126">Lambda – výrazy nemůže mít modifikátory, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="e1bf5-127">Lambda – výrazy nepoužívejte `As` klauzule k určení návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-127">Lambda expressions do not use an `As` clause to designate the return type of the function.</span></span> <span data-ttu-id="e1bf5-128">Místo toho je typ odvodit z hodnotu, která vyhodnotí jako text výrazu lambda jeden řádek, nebo vrací hodnotu výrazu lambda víceřádkový.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-128">Instead, the type is inferred from the value that the body of a single-line lambda expression evaluates to, or the return value of a multiline lambda expression.</span></span> <span data-ttu-id="e1bf5-129">Například, pokud je text výrazu lambda jeden řádek `Where cust.City = "London"`, je její návratový typ `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-129">For example, if the body of a single-line lambda expression is `Where cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="e1bf5-130">Tělo výrazu lambda jeden řádek musí být výraz není příkaz.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-130">The body of a single-line lambda expression must be an expression, not a statement.</span></span> <span data-ttu-id="e1bf5-131">Text se může skládat z volání procedury funkce, ale není volání procedury sub.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-131">The body can consist of a call to a function procedure, but not a call to a sub procedure.</span></span>  
  
-   <span data-ttu-id="e1bf5-132">Buď všechny parametry musí mít zadán odvodit datové typy nebo všechny.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-132">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="e1bf5-133">Volitelné a Paramarray parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-133">Optional and Paramarray parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="e1bf5-134">Obecné parametry nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-134">Generic parameters are not permitted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1bf5-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1bf5-135">Example</span></span>  
 <span data-ttu-id="e1bf5-136">Následující příklady ukazují dva způsoby, jak vytvořit jednoduché lambda – výrazy.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-136">The following examples show two ways to create simple lambda expressions.</span></span> <span data-ttu-id="e1bf5-137">První používá `Dim` k zadání názvu pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-137">The first uses a `Dim` to provide a name for the function.</span></span> <span data-ttu-id="e1bf5-138">Pro volání funkce, můžete odeslat hodnotu pro parametr.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-138">To call the function, you send in a value for the parameter.</span></span>  
  
 [!code-vb[VbVbalrLambdas#1](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="e1bf5-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1bf5-139">Example</span></span>  
 <span data-ttu-id="e1bf5-140">Alternativně můžete deklarovat a spusťte funkci ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-140">Alternatively, you can declare and run the function at the same time.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="e1bf5-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1bf5-141">Example</span></span>  
 <span data-ttu-id="e1bf5-142">Tady je příklad, který zvýší jeho argumentů a vrátí hodnotu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-142">Following is an example of a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="e1bf5-143">Příklad ukazuje, jak jeden řádek a víceřádkový syntaxe výrazu lambda pro funkci.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-143">The example shows both the single-line and multiline lambda expression syntax for a function.</span></span> <span data-ttu-id="e1bf5-144">Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e1bf5-144">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="e1bf5-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1bf5-145">Example</span></span>  
 <span data-ttu-id="e1bf5-146">Lambda – výrazy tvoří základ řadu operátory dotazu v [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]a je možné explicitně v dotazech na základě metod.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-146">Lambda expressions underlie many of the query operators in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)], and can be used explicitly in method-based queries.</span></span> <span data-ttu-id="e1bf5-147">Následující příklad ukazuje typické [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, za nímž následuje překlad dotazu do formátu metoda.</span><span class="sxs-lookup"><span data-stu-id="e1bf5-147">The following example shows a typical [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, followed by the translation of the query into method format.</span></span>  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 <span data-ttu-id="e1bf5-148">Další informace o metody dotazů najdete v tématu [dotazy](../../../visual-basic/language-reference/queries/queries.md).</span><span class="sxs-lookup"><span data-stu-id="e1bf5-148">For more information about query methods, see [Queries](../../../visual-basic/language-reference/queries/queries.md).</span></span> <span data-ttu-id="e1bf5-149">Další informace o standardních operátorů dotazu najdete v tématu [standardní přehled operátory dotazu](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e1bf5-149">For more information about standard query operators, see [Standard Query Operators Overview](../../programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1bf5-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1bf5-150">See Also</span></span>  
 [<span data-ttu-id="e1bf5-151">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="e1bf5-151">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="e1bf5-152">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="e1bf5-152">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="e1bf5-153">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="e1bf5-153">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="e1bf5-154">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e1bf5-154">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="e1bf5-155">Porovnání hodnot</span><span class="sxs-lookup"><span data-stu-id="e1bf5-155">Value Comparisons</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [<span data-ttu-id="e1bf5-156">Logické výrazy</span><span class="sxs-lookup"><span data-stu-id="e1bf5-156">Boolean Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [<span data-ttu-id="e1bf5-157">Operátor If</span><span class="sxs-lookup"><span data-stu-id="e1bf5-157">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="e1bf5-158">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="e1bf5-158">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
