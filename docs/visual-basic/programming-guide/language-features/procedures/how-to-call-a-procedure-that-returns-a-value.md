---
title: 'Postupy: Volání procedury, která vrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 6f45f01489ee84b6addb1f7c7c8dc584332f38dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333883"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="fcdf3-102">Postupy: Volání procedury, která vrací hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fcdf3-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="fcdf3-103">A `Function` postup vrací hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="fcdf3-104">Při volání včetně jejího názvu a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="fcdf3-105">Pro volání funkce ve výrazu</span><span class="sxs-lookup"><span data-stu-id="fcdf3-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="fcdf3-106">Použít `Function` postup pojmenovat stejně jako byste použili proměnné.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="fcdf3-107">Můžete použít `Function` volání procedur, kdekoli ve výrazu můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="fcdf3-108">Použijte název procedury se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="fcdf3-109">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="fcdf3-110">Však pomocí závorek díky váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="fcdf3-111">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="fcdf3-112">Je nutné zadat argumenty ve stejném pořadí, které `Function` procedura definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="fcdf3-113">Alternativně můžete předat jeden nebo více argumentů podle názvu.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="fcdf3-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="fcdf3-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="fcdf3-115">Hodnota vrácená z procedury podílí na výraz, stejně jako hodnota proměnné nebo by konstanty.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="fcdf3-116">Volat funkci proceduru v příkazu přiřazení</span><span class="sxs-lookup"><span data-stu-id="fcdf3-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="fcdf3-117">Použití `Function` název procedury po rovnosti (`=`) přihlaste příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="fcdf3-118">Použijte název procedury se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="fcdf3-119">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="fcdf3-120">Však pomocí závorek díky váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="fcdf3-121">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="fcdf3-122">Je nutné zadat argumenty ve stejném pořadí, které `Function` procedura definuje odpovídající parametry, pokud jsou byly předány podle názvu.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="fcdf3-123">Hodnota vrácená z procedury je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcdf3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="fcdf3-124">Example</span></span>  
 <span data-ttu-id="fcdf3-125">Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> k načtení hodnoty proměnné prostředí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="fcdf3-126">První řádek volá `Environ` v rámci výrazu a druhý řádek nazve je v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> `Environ` <span data-ttu-id="fcdf3-127">přijímá název proměnné jako její jediný argument.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-127">takes the variable name as its sole argument.</span></span> <span data-ttu-id="fcdf3-128">Vrátí hodnotu proměnné volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="fcdf3-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="fcdf3-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcdf3-129">See also</span></span>

- [<span data-ttu-id="fcdf3-130">Procedury Function</span><span class="sxs-lookup"><span data-stu-id="fcdf3-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="fcdf3-131">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="fcdf3-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fcdf3-132">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="fcdf3-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fcdf3-133">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="fcdf3-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="fcdf3-134">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="fcdf3-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="fcdf3-135">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="fcdf3-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
