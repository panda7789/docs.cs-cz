---
title: 'Postupy: Volání procedury, která vrátí hodnotu.'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], returning a value
ms.assetid: a445127b-0f5f-465a-98fb-3e514b93d115
ms.openlocfilehash: 7f5d46babf31ea3c6babb29c0f1c08a23e51d598
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340730"
---
# <a name="how-to-call-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="4ccc8-102">Postupy: Volání procedury, která vrátí hodnotu (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4ccc8-102">How to: Call a Procedure That Returns a Value (Visual Basic)</span></span>
<span data-ttu-id="4ccc8-103">Procedura `Function` vrátí hodnotu volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-103">A `Function` procedure returns a value to the calling code.</span></span> <span data-ttu-id="4ccc8-104">Zavoláte ho tak, že zahrnete jeho název a argumenty buď na pravé straně příkazu přiřazení, nebo ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-104">You call it by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span>  
  
### <a name="to-call-a-function-procedure-within-an-expression"></a><span data-ttu-id="4ccc8-105">Volání procedury funkce v rámci výrazu</span><span class="sxs-lookup"><span data-stu-id="4ccc8-105">To call a Function procedure within an expression</span></span>  
  
1. <span data-ttu-id="4ccc8-106">Použijte název `Function` procedury stejným způsobem jako při použití proměnné.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-106">Use the `Function` procedure name the same way you would use a variable.</span></span> <span data-ttu-id="4ccc8-107">Můžete použít volání procedury `Function` kdekoli, kde můžete použít proměnnou nebo konstantu ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-107">You can use a `Function` procedure call anywhere you can use a variable or constant in an expression.</span></span>  
  
2. <span data-ttu-id="4ccc8-108">Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="4ccc8-109">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="4ccc8-110">Použití závorek však usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="4ccc8-111">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="4ccc8-112">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` postup definuje odpovídající parametry.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-112">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="4ccc8-113">Alternativně můžete předat jeden nebo více argumentů podle názvu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-113">Alternatively, you can pass one or more arguments by name.</span></span> <span data-ttu-id="4ccc8-114">Další informace najdete v tématu [předávání argumentů podle pozice a názvu](./passing-arguments-by-position-and-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="4ccc8-114">For more information, see [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md).</span></span>  
  
4. <span data-ttu-id="4ccc8-115">Hodnota vrácená procedurou se účastní ve výrazu stejně jako hodnota proměnné nebo konstanty.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-115">The value returned from the procedure participates in the expression just as the value of a variable or constant would.</span></span>  
  
### <a name="to-call-a-function-procedure-in-an-assignment-statement"></a><span data-ttu-id="4ccc8-116">Volání procedury funkce v příkazu přiřazení</span><span class="sxs-lookup"><span data-stu-id="4ccc8-116">To call a Function procedure in an assignment statement</span></span>  
  
1. <span data-ttu-id="4ccc8-117">Použijte název `Function` procedury za znaménkem rovná se (`=`) v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-117">Use the `Function` procedure name following the equal (`=`) sign in the assignment statement.</span></span>  
  
2. <span data-ttu-id="4ccc8-118">Chcete-li uzavřít seznam argumentů, použijte název procedury s závorkami.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-118">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="4ccc8-119">Pokud neexistují žádné argumenty, můžete volitelně vynechat závorky.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-119">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="4ccc8-120">Použití závorek však usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-120">However, using the parentheses makes your code easier to read.</span></span>  
  
3. <span data-ttu-id="4ccc8-121">Argumenty umístěte do seznamu argumentů v závorkách a oddělte je čárkami.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-121">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="4ccc8-122">Ujistěte se, že jste zadali argumenty ve stejném pořadí, v jakém `Function` postup definuje odpovídající parametry, pokud je předáte podle názvu.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-122">Be sure you supply the arguments in the same order that the `Function` procedure defines the corresponding parameters, unless you are passing them by name.</span></span>  
  
4. <span data-ttu-id="4ccc8-123">Hodnota vrácená procedurou je uložena v proměnné nebo vlastnosti na levé straně příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-123">The value returned from the procedure is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ccc8-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ccc8-124">Example</span></span>  
 <span data-ttu-id="4ccc8-125">V následujícím příkladu je volána <xref:Microsoft.VisualBasic.Interaction.Environ%2A> Visual Basic pro načtení hodnoty proměnné prostředí operačního systému.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-125">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.Environ%2A> to retrieve the value of an operating system environment variable.</span></span> <span data-ttu-id="4ccc8-126">První řádek volá `Environ` v rámci výrazu a druhý řádek jej zavolá v příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-126">The first line calls `Environ` within an expression, and the second line calls it in an assignment statement.</span></span> <span data-ttu-id="4ccc8-127">`Environ` přebírá název proměnné jako jediný argument.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-127">`Environ` takes the variable name as its sole argument.</span></span> <span data-ttu-id="4ccc8-128">Vrátí hodnotu proměnné pro volající kód.</span><span class="sxs-lookup"><span data-stu-id="4ccc8-128">It returns the variable's value to the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="4ccc8-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ccc8-129">See also</span></span>

- [<span data-ttu-id="4ccc8-130">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="4ccc8-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="4ccc8-131">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="4ccc8-131">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="4ccc8-132">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="4ccc8-132">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="4ccc8-133">Postupy: Vytvoření procedury, která vrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="4ccc8-133">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="4ccc8-134">Postupy: Vrácení hodnoty z procedury</span><span class="sxs-lookup"><span data-stu-id="4ccc8-134">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="4ccc8-135">Postupy: Volání procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="4ccc8-135">How to: Call a Procedure that Does Not Return a Value</span></span>](./how-to-call-a-procedure-that-does-not-return-a-value.md)
