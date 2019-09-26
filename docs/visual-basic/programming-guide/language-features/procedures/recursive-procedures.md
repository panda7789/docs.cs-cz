---
title: Rekurzivní procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: b08a06a07f134b7c95251848862d39339e59fe61
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274346"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="6d690-102">Rekurzivní procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d690-102">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="6d690-103">*Rekurzivní* procedura je taková, která volá sám sebe.</span><span class="sxs-lookup"><span data-stu-id="6d690-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="6d690-104">Obecně to není nejúčinnější způsob psaní kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6d690-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="6d690-105">Následující postup používá rekurzi k výpočtu faktoriál jeho původního argumentu.</span><span class="sxs-lookup"><span data-stu-id="6d690-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="6d690-106">Otázky s rekurzivními procedurami</span><span class="sxs-lookup"><span data-stu-id="6d690-106">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="6d690-107">**Omezující podmínky**.</span><span class="sxs-lookup"><span data-stu-id="6d690-107">**Limiting Conditions**.</span></span> <span data-ttu-id="6d690-108">Je nutné navrhnout rekurzivní proceduru pro testování alespoň jedné podmínky, která může ukončit rekurzi, a také je třeba zpracovat případ, kdy není taková podmínka splněna v rozumném počtu rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="6d690-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="6d690-109">Bez nejméně jedné podmínky, která může být splněna bez selhání, váš postup bude mít vysoké riziko, že se spouští v nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="6d690-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="6d690-110">**Využití paměti**.</span><span class="sxs-lookup"><span data-stu-id="6d690-110">**Memory Usage**.</span></span> <span data-ttu-id="6d690-111">Vaše aplikace má omezené množství místa pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="6d690-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="6d690-112">Pokaždé, když procedura zavolá sám sebe, použije více místa pro další kopie místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="6d690-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="6d690-113">Pokud tento proces pokračuje neomezeně, způsobí <xref:System.StackOverflowException> to chybu.</span><span class="sxs-lookup"><span data-stu-id="6d690-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="6d690-114">**Efektivita**.</span><span class="sxs-lookup"><span data-stu-id="6d690-114">**Efficiency**.</span></span> <span data-ttu-id="6d690-115">Je možné, že téměř vždy nahradíte smyčku pro rekurzi.</span><span class="sxs-lookup"><span data-stu-id="6d690-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="6d690-116">Smyčka nemá režijní náklady na předávání argumentů, inicializaci dalšího úložiště a vrácení hodnot.</span><span class="sxs-lookup"><span data-stu-id="6d690-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="6d690-117">Výkon může být mnohem lepší bez rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="6d690-117">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="6d690-118">**Vzájemná rekurze**.</span><span class="sxs-lookup"><span data-stu-id="6d690-118">**Mutual Recursion**.</span></span> <span data-ttu-id="6d690-119">Můžete sledovat velmi špatný výkon nebo dokonce nekonečnou smyčku, pokud dva postupy navzájem volají.</span><span class="sxs-lookup"><span data-stu-id="6d690-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="6d690-120">Takový návrh představuje stejné problémy jako jeden rekurzivní postup, ale může být těžší detekovat a ladit.</span><span class="sxs-lookup"><span data-stu-id="6d690-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="6d690-121">**Volání pomocí závorek**.</span><span class="sxs-lookup"><span data-stu-id="6d690-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="6d690-122">Při rekurzivním volání procedury je nutné použít název procedury s závorkami, a to i v případě, že neexistuje seznam argumentů. `Function`</span><span class="sxs-lookup"><span data-stu-id="6d690-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="6d690-123">V opačném případě se název funkce povede jako reprezentace návratové hodnoty funkce.</span><span class="sxs-lookup"><span data-stu-id="6d690-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="6d690-124">**Testování**.</span><span class="sxs-lookup"><span data-stu-id="6d690-124">**Testing**.</span></span> <span data-ttu-id="6d690-125">Pokud zapíšete rekurzivní proceduru, měli byste je pečlivě otestovat, abyste se ujistili, že vždy splňují určitou omezující podmínku.</span><span class="sxs-lookup"><span data-stu-id="6d690-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="6d690-126">Měli byste taky zajistit, aby nedošlo k nedostatku paměti z důvodu příliš velkého počtu rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="6d690-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d690-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d690-127">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="6d690-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="6d690-128">Procedures</span></span>](index.md)
- [<span data-ttu-id="6d690-129">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="6d690-129">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="6d690-130">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="6d690-130">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="6d690-131">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6d690-131">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="6d690-132">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="6d690-132">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="6d690-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="6d690-133">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6d690-134">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="6d690-134">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="6d690-135">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="6d690-135">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="6d690-136">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="6d690-136">Loop Structures</span></span>](../control-flow/loop-structures.md)
