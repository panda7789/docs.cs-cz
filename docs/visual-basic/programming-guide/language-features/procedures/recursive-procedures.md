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
ms.openlocfilehash: 1802785e38b58ce2c057d6ddbe1e54e73e079761
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54660720"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="a7b04-102">Rekurzivní procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7b04-102">Recursive Procedures (Visual Basic)</span></span>
<span data-ttu-id="a7b04-103">A *rekurzivní* postup je takový, který zavolá sama sebe.</span><span class="sxs-lookup"><span data-stu-id="a7b04-103">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="a7b04-104">Většinou to není nejúčinnější způsob psaní kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a7b04-104">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="a7b04-105">Následující postup používá rekurze pro výpočet faktoriálu původní argument.</span><span class="sxs-lookup"><span data-stu-id="a7b04-105">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="a7b04-106">Informace o rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="a7b04-106">Considerations with Recursive Procedures</span></span>  
 <span data-ttu-id="a7b04-107">**Omezující podmínky**.</span><span class="sxs-lookup"><span data-stu-id="a7b04-107">**Limiting Conditions**.</span></span> <span data-ttu-id="a7b04-108">Je třeba navrhnout rekurzivní procedury pro testování nejméně jedné podmínky, které dokáže ukončit rekurze, a také musí zpracovávat tento případ, ve kterém je splněna žádná z těchto podmínek v rámci dostatečný počet rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="a7b04-108">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="a7b04-109">Bez nejméně jedné podmínky, které mohou být splněny bez navrácení služeb po spuštění procedury vysokým rizikem provedení v nekonečné smyčce.</span><span class="sxs-lookup"><span data-stu-id="a7b04-109">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>  
  
 <span data-ttu-id="a7b04-110">**Využití paměti**.</span><span class="sxs-lookup"><span data-stu-id="a7b04-110">**Memory Usage**.</span></span> <span data-ttu-id="a7b04-111">Vaše aplikace má omezené množství místa pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="a7b04-111">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="a7b04-112">Pokaždé, když procedury zavolá sama sebe, používá více toto místo pro další kopie, které své místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="a7b04-112">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="a7b04-113">Pokud tento proces pokračuje po neomezenou dobu, nakonec způsobí <xref:System.StackOverflowException> chyby.</span><span class="sxs-lookup"><span data-stu-id="a7b04-113">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>  
  
 <span data-ttu-id="a7b04-114">**Efektivita**.</span><span class="sxs-lookup"><span data-stu-id="a7b04-114">**Efficiency**.</span></span> <span data-ttu-id="a7b04-115">Můžete nahradit téměř vždy smyčku rekurze.</span><span class="sxs-lookup"><span data-stu-id="a7b04-115">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="a7b04-116">Smyčka nemá režii předávání argumentů, inicializace úložiště a vrací hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a7b04-116">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="a7b04-117">Výkon může být mnohem lepší bez rekurzivní volání.</span><span class="sxs-lookup"><span data-stu-id="a7b04-117">Your performance can be much better without recursive calls.</span></span>  
  
 <span data-ttu-id="a7b04-118">**Vzájemná rekurze**.</span><span class="sxs-lookup"><span data-stu-id="a7b04-118">**Mutual Recursion**.</span></span> <span data-ttu-id="a7b04-119">Velmi nízký výkon nebo dokonce nekonečnou smyčku, všimnout dva postupy volání mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="a7b04-119">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="a7b04-120">Takový návrh stejným problémům jako v postupu jeden rekurzivní uvede, ale může být obtížnější rozpoznání a ladění.</span><span class="sxs-lookup"><span data-stu-id="a7b04-120">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>  
  
 <span data-ttu-id="a7b04-121">**Volání se závorkami**.</span><span class="sxs-lookup"><span data-stu-id="a7b04-121">**Calling with Parentheses**.</span></span> <span data-ttu-id="a7b04-122">Když `Function` proceduru volá rekurzivně sama sebe, je nutné postupovat podle název procedury se závorkami, i v případě, že neexistuje žádný seznam argumentů.</span><span class="sxs-lookup"><span data-stu-id="a7b04-122">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="a7b04-123">V opačném případě je název funkce používá jako návratový typ funkce.</span><span class="sxs-lookup"><span data-stu-id="a7b04-123">Otherwise, the function name is taken as representing the return value of the function.</span></span>  
  
 <span data-ttu-id="a7b04-124">**Testování**.</span><span class="sxs-lookup"><span data-stu-id="a7b04-124">**Testing**.</span></span> <span data-ttu-id="a7b04-125">Pokud píšete rekurzivní procedury, měli byste ho otestovat velmi pečlivě zajistit, aby že vždy splňuje některé omezující podmínky.</span><span class="sxs-lookup"><span data-stu-id="a7b04-125">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="a7b04-126">Také se ujistěte, že nelze spustit nedostatek paměti z důvodu existence příliš mnoho rekurzivních volání.</span><span class="sxs-lookup"><span data-stu-id="a7b04-126">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b04-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7b04-127">See also</span></span>
- <xref:System.StackOverflowException>
- [<span data-ttu-id="a7b04-128">Procedury</span><span class="sxs-lookup"><span data-stu-id="a7b04-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="a7b04-129">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="a7b04-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="a7b04-130">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="a7b04-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="a7b04-131">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a7b04-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="a7b04-132">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a7b04-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a7b04-133">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="a7b04-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="a7b04-134">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="a7b04-134">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="a7b04-135">Řešení potíží s procedurami</span><span class="sxs-lookup"><span data-stu-id="a7b04-135">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="a7b04-136">Struktury smyčky</span><span class="sxs-lookup"><span data-stu-id="a7b04-136">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="a7b04-137">Řešení potíží s výjimkami: System.StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="a7b04-137">Troubleshooting Exceptions: System.StackOverflowException</span></span>](https://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
