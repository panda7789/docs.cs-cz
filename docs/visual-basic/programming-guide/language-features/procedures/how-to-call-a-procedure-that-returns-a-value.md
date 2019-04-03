---
title: 'Postupy: Volání procedury, která vrací hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: ee80ae48a9b9bfae0afe8f0a2c6e7ebf047d9d36
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820383"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="30dab-102">Postupy: Volání procedury, která vrací hodnotu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30dab-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="30dab-103">A `Function` postup vrací hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="30dab-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="30dab-104">Při volání včetně jejího názvu a argumenty buď na pravé straně příkazu přiřazení nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="30dab-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="30dab-105">Pro volání funkce ve výrazu</span><span class="sxs-lookup"><span data-stu-id="30dab-105">To call a Function procedure within an expression</span></span>  
  
1.  <span data-ttu-id="30dab-106">Použít `Function` postup pojmenovat stejně jako byste použili proměnné.</span><span class="sxs-lookup"><span data-stu-id="30dab-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="30dab-107">Můžete použít `Function` volání procedur, kdekoli ve výrazu můžete použít proměnnou nebo konstantu.</span><span class="sxs-lookup"><span data-stu-id="30dab-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2.  <span data-ttu-id="30dab-108">Použijte název procedury se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="30dab-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="30dab-109">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="30dab-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="30dab-110">Však pomocí závorek díky váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="30dab-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="30dab-111">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="30dab-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="30dab-112">Je nutné zadat argumenty ve stejném pořadí, které `Function` procedura definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="30dab-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="30dab-113">Alternativně můžete předat jeden nebo více argumentů podle názvu.</span><span class="sxs-lookup"><span data-stu-id="30dab-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="30dab-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="30dab-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4.  <span data-ttu-id="30dab-115">Hodnota vrácená z procedury podílí na výraz, stejně jako hodnota proměnné nebo by konstanty.</span><span class="sxs-lookup"><span data-stu-id="30dab-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="30dab-116">Volat funkci proceduru v příkazu přiřazení</span><span class="sxs-lookup"><span data-stu-id="30dab-116">To call a Function procedure in an assignment statement</span></span>  
  
1.  <span data-ttu-id="30dab-117">Použití `Function` název procedury po rovnosti (`=`) přihlaste příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="30dab-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2.  <span data-ttu-id="30dab-118">Použijte název procedury se závorkami uvést seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="30dab-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="30dab-119">Pokud neexistují žádné argumenty, můžete volitelně vynechejte závorky.</span><span class="sxs-lookup"><span data-stu-id="30dab-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="30dab-120">Však pomocí závorek díky váš kód lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="30dab-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="30dab-121">Umístěte argumenty v seznamu argumentů v závorkách, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="30dab-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="30dab-122">Je nutné zadat argumenty ve stejném pořadí, které `Function` procedura definuje odpovídající parametry, pokud jsou byly předány podle názvu.</span><span class="sxs-lookup"><span data-stu-id="30dab-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4.  <span data-ttu-id="30dab-123">Hodnota vrácená z procedury je uložen v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="30dab-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30dab-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="30dab-124">Example</span></span>  
 <span data-ttu-id="30dab-125">Následující příklad volá jazyka Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> k načtení hodnoty proměnné prostředí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="30dab-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="30dab-126">První řádek volá `Environ` v rámci výrazu a druhý řádek nazve je v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="30dab-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="30dab-127">`Environ` přijímá název proměnné jako její jediný argument.</span><span class="sxs-lookup"><span data-stu-id="30dab-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="30dab-128">Vrátí hodnotu proměnné volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="30dab-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="30dab-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30dab-129">See also</span></span>

- [<span data-ttu-id="30dab-130">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="30dab-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="30dab-131">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="30dab-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="30dab-132">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="30dab-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="30dab-133">Postupy: Vytvořit proceduru, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="30dab-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="30dab-134">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="30dab-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="30dab-135">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="30dab-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
