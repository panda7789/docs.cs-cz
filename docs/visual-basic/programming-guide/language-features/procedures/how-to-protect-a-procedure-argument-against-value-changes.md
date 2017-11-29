---
title: "Postupy: Ochrana argumentu procedury proti změnám hodnoty (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="dd108-102">Postupy: Ochrana argumentu procedury proti změnám hodnoty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd108-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="dd108-103">Pokud procedury deklaruje parametr jako [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] poskytuje kód postup přímý odkaz na programovací element základní argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="dd108-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="dd108-104">To umožňuje postup změňte hodnotu základní argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="dd108-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="dd108-105">V některých případech může volající kód chcete chránit proti takové změny.</span><span class="sxs-lookup"><span data-stu-id="dd108-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="dd108-106">Vždy můžete chránit argument z změnu deklarováním odpovídající parametr [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) v postupu.</span><span class="sxs-lookup"><span data-stu-id="dd108-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="dd108-107">Pokud chcete změnit zadaný argument v některých případech ale jiné ne, je možné deklarovat `ByRef` a nechat kód volání určit mechanismus předávání při každém volání.</span><span class="sxs-lookup"><span data-stu-id="dd108-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="dd108-108">Dělá to pomocí uzavření odpovídající argument v závorkách k předání hodnotou nebo není uveden v závorkách k předání odkazem.</span><span class="sxs-lookup"><span data-stu-id="dd108-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="dd108-109">Další informace najdete v tématu [postupy: vynucení předání hodnotou argumentu](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="dd108-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd108-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd108-110">Example</span></span>  
 <span data-ttu-id="dd108-111">Následující příklad ukazuje dva postupy, které provádějí proměnné pole a pracovat na jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="dd108-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="dd108-112">`increase` Postup jednoduše přidá jeden na každý element.</span><span class="sxs-lookup"><span data-stu-id="dd108-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="dd108-113">`replace` Postup přiřadí nové pole do parametru `a()` a potom přidá jeden na každý element.</span><span class="sxs-lookup"><span data-stu-id="dd108-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="dd108-114">Opětovné přiřazení neovlivňuje základní proměnné pole v volající kód.</span><span class="sxs-lookup"><span data-stu-id="dd108-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 <span data-ttu-id="dd108-115">První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="dd108-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="dd108-116">Protože pole `n` je typu odkazu `replace` můžete změnit její členy, i když tento mechanismus předávání `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="dd108-116">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="dd108-117">Druhý `MsgBox` volání zobrazí "po replace(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="dd108-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="dd108-118">Protože `n` je předán `ByVal`, `replace` nelze upravit proměnnou `n` v kód volání přiřazením nové pole.</span><span class="sxs-lookup"><span data-stu-id="dd108-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="dd108-119">Když `replace` vytvoří novou instanci pole `k` a přiřadí ji k místní proměnné `a`, se ztratí odkaz na `n` předaná volající kódem.</span><span class="sxs-lookup"><span data-stu-id="dd108-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="dd108-120">Po změně členů `a`, pouze místní pole `k` má vliv.</span><span class="sxs-lookup"><span data-stu-id="dd108-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="dd108-121">Proto `replace` nezvyšuje hodnoty pole `n` v volání kódu.</span><span class="sxs-lookup"><span data-stu-id="dd108-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd108-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dd108-122">Compiling the Code</span></span>  
 <span data-ttu-id="dd108-123">Výchozí hodnota v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je předání argumentů hodnotou.</span><span class="sxs-lookup"><span data-stu-id="dd108-123">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="dd108-124">Ale je dobrým zvykem obsahovat buď programovacím [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="dd108-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="dd108-125">To výrazně zjednodušuje kódu ke čtení.</span><span class="sxs-lookup"><span data-stu-id="dd108-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd108-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd108-126">See Also</span></span>  
 [<span data-ttu-id="dd108-127">Postupy</span><span class="sxs-lookup"><span data-stu-id="dd108-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="dd108-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="dd108-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="dd108-129">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="dd108-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="dd108-130">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="dd108-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="dd108-131">Rozdíly mezi upravitelnými a Neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="dd108-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="dd108-132">Rozdíly mezi předáním argumentu podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="dd108-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="dd108-133">Postupy: Změna hodnoty argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="dd108-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="dd108-134">Postupy: vynucení předání hodnotou argumentu</span><span class="sxs-lookup"><span data-stu-id="dd108-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="dd108-135">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="dd108-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="dd108-136">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="dd108-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
