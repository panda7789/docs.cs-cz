---
title: 'Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 35f757609b6d0b36652db3b14e62ecd299a063ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649409"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="2523f-102">Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="2523f-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="2523f-103">A `Function` postup vrátí hodnotu volání kódu.</span><span class="sxs-lookup"><span data-stu-id="2523f-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="2523f-104">Můžete pro volání ho včetně jeho název a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="2523f-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="2523f-105">K volání procedury, funkce v rámci výrazu</span><span class="sxs-lookup"><span data-stu-id="2523f-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="2523f-106">Použít `Function` postupu název stejným způsobem jako použijete proměnnou.</span><span class="sxs-lookup"><span data-stu-id="2523f-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="2523f-107">Můžete použít `Function` volání procedur, kdekoli proměnnou nebo konstanta můžete použít ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="2523f-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="2523f-108">Použijte název procedury v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="2523f-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2523f-109">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="2523f-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2523f-110">Však pomocí závorek usnadňuje kódu čtení.</span><span class="sxs-lookup"><span data-stu-id="2523f-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="2523f-111">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="2523f-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2523f-112">Ujistěte se, zadejte argumenty ve stejném pořadí, `Function` postupu definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="2523f-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="2523f-113">Alternativně můžete předat jeden nebo více argumentů podle názvu.</span><span class="sxs-lookup"><span data-stu-id="2523f-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="2523f-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="2523f-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="2523f-115">Hodnota vrácená z procesu účastní výraz stejně jako hodnota proměnné nebo by konstanta.</span><span class="sxs-lookup"><span data-stu-id="2523f-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="2523f-116">K volání procedury, funkce v příkazu přiřazení</span><span class="sxs-lookup"><span data-stu-id="2523f-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="2523f-117">Použití `Function` název procedury následující rovno (`=`) přihlásit příkaz přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2523f-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="2523f-118">Použijte název procedury v závorkách uveďte seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="2523f-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="2523f-119">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorkách.</span><span class="sxs-lookup"><span data-stu-id="2523f-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="2523f-120">Však pomocí závorek usnadňuje kódu čtení.</span><span class="sxs-lookup"><span data-stu-id="2523f-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="2523f-121">Umístěte argumenty v seznamu argumentů v závorkách, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="2523f-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="2523f-122">Ujistěte se, zadejte argumenty ve stejném pořadí, `Function` postupu definuje odpovídajících parametrů, pokud jsou jejich předání podle názvu.</span><span class="sxs-lookup"><span data-stu-id="2523f-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="2523f-123">Hodnota vrácená v postupu je uložené v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2523f-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2523f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2523f-124">Example</span></span>  
 <span data-ttu-id="2523f-125">V následujícím příkladu volání jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> k načtení hodnoty proměnné prostředí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2523f-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="2523f-126">První řádek volání `Environ` ve výrazu a druhý řádek nazve je v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="2523f-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="2523f-127">`Environ` přebírá název proměnné jako jedinou argument.</span><span class="sxs-lookup"><span data-stu-id="2523f-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="2523f-128">Hodnota proměnné vrátí volání kódu.</span><span class="sxs-lookup"><span data-stu-id="2523f-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](./codesnippet/VisualBasic/how-to-call-a-procedure-that-returns-a-value_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2523f-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="2523f-129">See Also</span></span>  
 [<span data-ttu-id="2523f-130">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="2523f-130">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="2523f-131">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="2523f-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="2523f-132">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="2523f-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="2523f-133">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="2523f-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)  
 [<span data-ttu-id="2523f-134">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="2523f-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)  
 [<span data-ttu-id="2523f-135">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="2523f-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
