---
title: Sub – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 602212e664fa3362742fb1ba0dc033610272d3af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603532"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="e18cf-102">Sub – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e18cf-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="e18cf-103">Deklaruje, parametry a kód, který definovat podprogramu výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="e18cf-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e18cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e18cf-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="e18cf-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="e18cf-105">Parts</span></span>  
  
|<span data-ttu-id="e18cf-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e18cf-106">Term</span></span>|<span data-ttu-id="e18cf-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e18cf-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="e18cf-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e18cf-108">Optional.</span></span> <span data-ttu-id="e18cf-109">Seznam místní názvy proměnných, které představují parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="e18cf-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="e18cf-110">Závorkách musí být k dispozici i v případě, že seznam je prázdný.</span><span class="sxs-lookup"><span data-stu-id="e18cf-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="e18cf-111">Další informace najdete v tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="e18cf-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="e18cf-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e18cf-112">Required.</span></span> <span data-ttu-id="e18cf-113">Jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="e18cf-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="e18cf-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e18cf-114">Required.</span></span> <span data-ttu-id="e18cf-115">Seznam příkazů.</span><span class="sxs-lookup"><span data-stu-id="e18cf-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e18cf-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e18cf-116">Remarks</span></span>  
 <span data-ttu-id="e18cf-117">A *výrazu lambda* je podprogramu, který nemá název a které provede jeden nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="e18cf-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="e18cf-118">Výraz lambda lze použít kdekoli používané typem delegáta, s výjimkou jako argument pro `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="e18cf-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="e18cf-119">Další informace o Delegáti a použití výrazů lambda s delegáti najdete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="e18cf-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="e18cf-120">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="e18cf-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="e18cf-121">Syntaxe výrazu lambda podobá se standardní podprogramu.</span><span class="sxs-lookup"><span data-stu-id="e18cf-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="e18cf-122">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e18cf-122">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="e18cf-123">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="e18cf-123">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="e18cf-124">Výraz lambda nemůže mít modifikátor, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="e18cf-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="e18cf-125">Tělo výrazu lambda jeden řádek musí být příkaz, není výraz.</span><span class="sxs-lookup"><span data-stu-id="e18cf-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="e18cf-126">Text se může skládat z volání procedury sub, ale není volání procedury funkce.</span><span class="sxs-lookup"><span data-stu-id="e18cf-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
-   <span data-ttu-id="e18cf-127">Ve výrazu lambda buď všechny parametry musí mít zadán odvodit datové typy nebo všechny parametry.</span><span class="sxs-lookup"><span data-stu-id="e18cf-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
-   <span data-ttu-id="e18cf-128">Volitelné a `ParamArray` parametry nejsou povoleny ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="e18cf-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
-   <span data-ttu-id="e18cf-129">Obecné parametry nejsou povoleny ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="e18cf-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e18cf-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="e18cf-130">Example</span></span>  
 <span data-ttu-id="e18cf-131">Tady je příklad výrazu lambda, která hodnotu zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e18cf-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="e18cf-132">Příklad ukazuje, jak jeden řádek a víceřádkový syntaxe výrazu lambda pro podprogramu.</span><span class="sxs-lookup"><span data-stu-id="e18cf-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="e18cf-133">Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="e18cf-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/sub-expression_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e18cf-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e18cf-134">See Also</span></span>  
 [<span data-ttu-id="e18cf-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="e18cf-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="e18cf-136">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="e18cf-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="e18cf-137">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="e18cf-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="e18cf-138">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e18cf-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="e18cf-139">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="e18cf-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
