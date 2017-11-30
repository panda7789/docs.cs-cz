---
title: "Postupy: Volání procedury, která vrátí hodnotu (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f6d408eed67fa417f42252bb49ecea28d4458382
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="d6233-102">Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="d6233-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="d6233-103">A `Function` postup vrátí hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="d6233-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="d6233-104">Můžete pro volání ho včetně jeho název a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="d6233-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="d6233-105">K volání procedury, funkce v rámci výrazu</span><span class="sxs-lookup"><span data-stu-id="d6233-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="d6233-106">Použít `Function` postupu název stejným způsobem jako použijete proměnnou.</span><span class="sxs-lookup"><span data-stu-id="d6233-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="d6233-107">Můžete použít `Function` volání procedur, kdekoli proměnnou nebo konstanta můžete použít ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="d6233-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="d6233-108">Použijte název procedury v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="d6233-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d6233-109">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="d6233-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="d6233-110">Však pomocí závorek usnadňuje kódu čtení.</span><span class="sxs-lookup"><span data-stu-id="d6233-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="d6233-111">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="d6233-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d6233-112">Ujistěte se, zadejte argumenty ve stejném pořadí, `Function` postupu definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="d6233-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="d6233-113">Alternativně můžete předat jeden nebo více argumentů podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d6233-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="d6233-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="d6233-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="d6233-115">Hodnota vrácená z procesu účastní výraz stejně jako hodnota proměnné nebo by konstanta.</span><span class="sxs-lookup"><span data-stu-id="d6233-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="d6233-116">K volání procedury, funkce v příkazu přiřazení</span><span class="sxs-lookup"><span data-stu-id="d6233-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="d6233-117">Použití `Function` název procedury následující rovno (`=`) přihlásit příkaz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d6233-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="d6233-118">Použijte název procedury v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="d6233-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="d6233-119">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="d6233-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="d6233-120">Však pomocí závorek usnadňuje kódu čtení.</span><span class="sxs-lookup"><span data-stu-id="d6233-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="d6233-121">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="d6233-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="d6233-122">Ujistěte se, zadejte argumenty ve stejném pořadí, `Function` postupu definuje odpovídajících parametrů, pokud jsou jejich předání podle názvu.</span><span class="sxs-lookup"><span data-stu-id="d6233-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="d6233-123">Hodnota vrácená v postupu je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d6233-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6233-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6233-124">Example</span></span>  
 <span data-ttu-id="d6233-125">Následující příklad volání [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> k načtení hodnoty proměnné prostředí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="d6233-125">The following example calls the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="d6233-126">První řádek volání `Environ` ve výrazu a druhý řádek nazve je v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="d6233-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="d6233-127">`Environ`přebírá název proměnné jako jedinou argument.</span><span class="sxs-lookup"><span data-stu-id="d6233-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="d6233-128">Hodnota proměnné vrátí volání kódu.</span><span class="sxs-lookup"><span data-stu-id="d6233-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d6233-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6233-129">See Also</span></span>  
 [<span data-ttu-id="d6233-130">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="d6233-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="d6233-131">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="d6233-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d6233-132">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="d6233-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="d6233-133">Postupy: vytvoření procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="d6233-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="d6233-134">Postupy: vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="d6233-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="d6233-135">Postupy: volání procedury, která nevrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="d6233-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
