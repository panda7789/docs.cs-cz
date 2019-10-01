---
title: Sub – výraz (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 2330b410f54b54d8f6cb7d8ad6f9b39a3f4d31bc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701340"
---
# <a name="sub-expression-visual-basic"></a><span data-ttu-id="08892-102">Sub – výraz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08892-102">Sub Expression (Visual Basic)</span></span>
<span data-ttu-id="08892-103">Deklaruje parametry a kód definující výraz subrutiny lambda.</span><span class="sxs-lookup"><span data-stu-id="08892-103">Declares the parameters and code that define a subroutine lambda expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08892-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08892-104">Syntax</span></span>  
  
```vb  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="08892-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="08892-105">Parts</span></span>  
  
|<span data-ttu-id="08892-106">Termín</span><span class="sxs-lookup"><span data-stu-id="08892-106">Term</span></span>|<span data-ttu-id="08892-107">Definice</span><span class="sxs-lookup"><span data-stu-id="08892-107">Definition</span></span>|  
|---|---|  
|`parameterlist`|<span data-ttu-id="08892-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="08892-108">Optional.</span></span> <span data-ttu-id="08892-109">Seznam místních názvů proměnných, které reprezentují parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="08892-109">A list of local variable names that represent the parameters of the procedure.</span></span> <span data-ttu-id="08892-110">Závorky musí být přítomny i v případě, že je seznam prázdný.</span><span class="sxs-lookup"><span data-stu-id="08892-110">The parentheses must be present even when the list is empty.</span></span> <span data-ttu-id="08892-111">Další informace najdete v tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="08892-111">For more information, see [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`statement`|<span data-ttu-id="08892-112">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="08892-112">Required.</span></span> <span data-ttu-id="08892-113">Jediný příkaz.</span><span class="sxs-lookup"><span data-stu-id="08892-113">A single statement.</span></span>|  
|`statements`|<span data-ttu-id="08892-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="08892-114">Required.</span></span> <span data-ttu-id="08892-115">Seznam příkazů.</span><span class="sxs-lookup"><span data-stu-id="08892-115">A list of statements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08892-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08892-116">Remarks</span></span>  
 <span data-ttu-id="08892-117">*Výraz lambda* je podprogram, který nemá název a který provádí jeden nebo více příkazů.</span><span class="sxs-lookup"><span data-stu-id="08892-117">A *lambda expression* is a subroutine that does not have a name and that executes one or more statements.</span></span> <span data-ttu-id="08892-118">Můžete použít výraz lambda kdekoli, kde můžete použít typ delegáta, s výjimkou argumentu pro `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="08892-118">You can use a lambda expression anywhere that you can use a delegate type, except as an argument to `RemoveHandler`.</span></span> <span data-ttu-id="08892-119">Další informace o delegátech a použití výrazů lambda s delegáty naleznete v tématu [příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) a [odlehčený převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="08892-119">For more information about delegates, and the use of lambda expressions with delegates, see [Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md) and [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="08892-120">Syntaxe výrazu lambda</span><span class="sxs-lookup"><span data-stu-id="08892-120">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="08892-121">Syntaxe výrazu lambda se podobá standardní podrutině.</span><span class="sxs-lookup"><span data-stu-id="08892-121">The syntax of a lambda expression resembles that of a standard subroutine.</span></span> <span data-ttu-id="08892-122">Rozdíly jsou následující:</span><span class="sxs-lookup"><span data-stu-id="08892-122">The differences are as follows:</span></span>  
  
- <span data-ttu-id="08892-123">Výraz lambda nemá název.</span><span class="sxs-lookup"><span data-stu-id="08892-123">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="08892-124">Výraz lambda nemůže obsahovat modifikátor, například `Overloads` nebo `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="08892-124">A lambda expression cannot have a modifier, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="08892-125">Tělo výrazu lambda s jedním řádkem musí být příkaz, nikoli výraz.</span><span class="sxs-lookup"><span data-stu-id="08892-125">The body of a single-line lambda expression must be a statement, not an expression.</span></span> <span data-ttu-id="08892-126">Tělo může být tvořeno voláním procedury Sub, ale nikoli voláním procedury funkce.</span><span class="sxs-lookup"><span data-stu-id="08892-126">The body can consist of a call to a sub procedure, but not a call to a function procedure.</span></span>  
  
- <span data-ttu-id="08892-127">Ve výrazu lambda musí mít buď všechny parametry zadané datové typy, nebo musí být všechny parametry odvozeny.</span><span class="sxs-lookup"><span data-stu-id="08892-127">In a lambda expression, either all parameters must have specified data types or all parameters must be inferred.</span></span>  
  
- <span data-ttu-id="08892-128">Volitelné parametry a parametry `ParamArray` nejsou ve výrazech lambda povoleny.</span><span class="sxs-lookup"><span data-stu-id="08892-128">Optional and `ParamArray` parameters are not permitted in lambda expressions.</span></span>  
  
- <span data-ttu-id="08892-129">Obecné parametry nejsou ve výrazech lambda povoleny.</span><span class="sxs-lookup"><span data-stu-id="08892-129">Generic parameters are not permitted in lambda expressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08892-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="08892-130">Example</span></span>  
 <span data-ttu-id="08892-131">Následuje příklad výrazu lambda, který zapisuje hodnotu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="08892-131">Following is an example of a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="08892-132">V příkladu se zobrazuje jak jednoduchá, tak víceřádková syntaxe výrazu lambda pro podprogram.</span><span class="sxs-lookup"><span data-stu-id="08892-132">The example shows both the single-line and multiline lambda expression syntax for a subroutine.</span></span> <span data-ttu-id="08892-133">Další příklady naleznete v tématu [lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="08892-133">For more examples, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="08892-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08892-134">See also</span></span>

- [<span data-ttu-id="08892-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="08892-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="08892-136">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="08892-136">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="08892-137">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="08892-137">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="08892-138">Příkazy</span><span class="sxs-lookup"><span data-stu-id="08892-138">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
- [<span data-ttu-id="08892-139">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="08892-139">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
