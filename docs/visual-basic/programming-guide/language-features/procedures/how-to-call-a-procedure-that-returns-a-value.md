---
title: 'Postupy: Volání procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: a110cf9f3b42c7244d8d5bf7b49d5e6dac8c2e21
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388761"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="72bed-102">Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="72bed-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="72bed-103">`Function`Procedura vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="72bed-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="72bed-104">Zavoláte ho tak, že zahrnete jeho název a argumenty buď na pravé straně příkazu přiřazení, nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="72bed-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="72bed-105">Volání procedury funkce v rámci výrazu</span><span class="sxs-lookup"><span data-stu-id="72bed-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="72bed-106">Použijte `Function` název procedury stejným způsobem, jako byste použili proměnnou.</span><span class="sxs-lookup"><span data-stu-id="72bed-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="72bed-107">Můžete použít `Function` volání procedury kdekoliv, kde můžete použít proměnnou nebo konstantu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="72bed-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="72bed-108">Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami.</span><span class="sxs-lookup"><span data-stu-id="72bed-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="72bed-109">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="72bed-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="72bed-110">Použití závorek však usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="72bed-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="72bed-111">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="72bed-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="72bed-112">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` procedura definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="72bed-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="72bed-113">Alternativně můžete předat jeden nebo více argumentů podle názvu.</span><span class="sxs-lookup"><span data-stu-id="72bed-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="72bed-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="72bed-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="72bed-115">Hodnota vrácená procedurou se účastní ve výrazu stejně jako hodnota proměnné nebo konstanty.</span><span class="sxs-lookup"><span data-stu-id="72bed-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="72bed-116">Volání procedury funkce v příkazu přiřazení</span><span class="sxs-lookup"><span data-stu-id="72bed-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="72bed-117">Použijte `Function` název procedury za znaménkem EQUAL ( `=` ) v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="72bed-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="72bed-118">Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami.</span><span class="sxs-lookup"><span data-stu-id="72bed-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="72bed-119">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="72bed-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="72bed-120">Použití závorek však usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="72bed-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="72bed-121">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="72bed-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="72bed-122">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` procedura definuje odpovídající parametry, pokud je předáte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="72bed-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="72bed-123">Hodnota vrácená procedurou je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="72bed-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72bed-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="72bed-124">Example</span></span>  
 <span data-ttu-id="72bed-125">Následující příklad volá Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> pro načtení hodnoty proměnné prostředí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="72bed-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="72bed-126">První řádek volá `Environ` v rámci výrazu a druhý řádek jej zavolá v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="72bed-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="72bed-127">`Environ`Převede název proměnné jako svůj jediný argument.</span><span class="sxs-lookup"><span data-stu-id="72bed-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="72bed-128">Vrátí hodnotu proměnné pro volající kód.</span><span class="sxs-lookup"><span data-stu-id="72bed-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="72bed-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="72bed-129">See also</span></span>

- [<span data-ttu-id="72bed-130">Procedury funkcí</span><span class="sxs-lookup"><span data-stu-id="72bed-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="72bed-131">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="72bed-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="72bed-132">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="72bed-132">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="72bed-133">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="72bed-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="72bed-134">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="72bed-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="72bed-135">Postupy: Volání procedury, která nevrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="72bed-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
