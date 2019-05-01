---
title: Sub – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 5b26a091dc8eb7415702c3c2853a569324def7d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013501"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="6d7f7-102">Sub – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d7f7-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="6d7f7-103">Deklaruje parametry a kód, které definují výrazu lambda podprogram.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d7f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d7f7-104">Syntax</span></span>  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="6d7f7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="6d7f7-105">Parts</span></span>  
  
|<span data-ttu-id="6d7f7-106">Termín</span><span class="sxs-lookup"><span data-stu-id="6d7f7-106">Term</span></span>|<span data-ttu-id="6d7f7-107">Definice</span><span class="sxs-lookup"><span data-stu-id="6d7f7-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="6d7f7-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-108">Optional.</span></span> <span data-ttu-id="6d7f7-109">Seznam místní názvy proměnných, které představují parametry procesu.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="6d7f7-110">Závorky musí být k dispozici i v případě, že je seznam prázdný.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="6d7f7-111">Další informace najdete v tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="6d7f7-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="6d7f7-112">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-112">Required.</span></span> <span data-ttu-id="6d7f7-113">Jeden příkaz.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="6d7f7-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-114">Required.</span></span> <span data-ttu-id="6d7f7-115">Seznam příkazů.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d7f7-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d7f7-116">Remarks</span></span>  
 <span data-ttu-id="6d7f7-117">A *výraz lambda* je podprogram, který nemá název a, který se spustí jeden nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="6d7f7-118">Výraz lambda můžete použít kdekoli, můžete použít typ delegáta, s výjimkou jako argument `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="6d7f7-119">Další informace o delegátech a použití výrazů lambda s delegáty, naleznete v tématu [delegáta příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md) a [volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="6d7f7-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="6d7f7-120">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="6d7f7-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="6d7f7-121">Syntaxe výrazu lambda se podobá u standardní podprogram.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="6d7f7-122">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6d7f7-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="6d7f7-123">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="6d7f7-124">Výraz lambda nemůže mít modifikátor, jako například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="6d7f7-125">Příkaz, není výraz musí být tělo tohoto výrazu lambda jednořádkového.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="6d7f7-126">Text se může skládat z volání procedury sub, ale není volání funkce procedury.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="6d7f7-127">Výraz lambda musí být buď všechny parametry zadána, že datové typy nebo všechny parametry musí být odvozený.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="6d7f7-128">Volitelné a `ParamArray` parametry nejsou povoleny ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="6d7f7-129">Obecné parametry nejsou povoleny ve výrazech lambda.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d7f7-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d7f7-130">Example</span></span>  
 <span data-ttu-id="6d7f7-131">Následuje příklad výrazu lambda, která hodnotu zapíše do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="6d7f7-132">Příklad ukazuje obě jedním řádkem a víceřádkového výrazu lambda výraz syntaxe podprogram.</span><span class="sxs-lookup"><span data-stu-id="6d7f7-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="6d7f7-133">Další příklady najdete v tématu [výrazy Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6d7f7-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="6d7f7-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d7f7-134">See also</span></span>

- [<span data-ttu-id="6d7f7-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="6d7f7-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6d7f7-136">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="6d7f7-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="6d7f7-137">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="6d7f7-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="6d7f7-138">Příkazy</span><span class="sxs-lookup"><span data-stu-id="6d7f7-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="6d7f7-139">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="6d7f7-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
