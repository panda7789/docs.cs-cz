---
title: "Postupy: Změna hodnoty argumentu procedury (Visual Basic)"
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba23c8f0b4b0b6e751546019af902a6305b9ef53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="ab5a0-102">Postupy: Změna hodnoty argumentu procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab5a0-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="ab5a0-103">Při volání procedury, všechny argumenty, které zadáte odpovídá jednomu z parametry definované v postupu.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="ab5a0-104">V některých případech můžete kód postupu změňte hodnotu základní argument volající kód.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="ab5a0-105">V ostatních případech postupu můžete změnit pouze místní kopie argument.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="ab5a0-106">Při volání procedury, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vytvoří místní kopii každý argument, který je předán [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="ab5a0-106">When you call the procedure, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="ab5a0-107">Pro každý argument předaný [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] poskytuje kód postup přímý odkaz na programovací element základní argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="ab5a0-108">Pokud základní element v volání kódu je upravitelnými a argument předaný `ByRef`, kód postup pomocí přímý odkaz můžete změnit hodnotu elementu v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="ab5a0-109">Změna základní hodnoty</span><span class="sxs-lookup"><span data-stu-id="ab5a0-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="ab5a0-110">Ke změně základní hodnoty argumentu procedury v volání kódu</span><span class="sxs-lookup"><span data-stu-id="ab5a0-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="ab5a0-111">V deklaraci postupu zadejte [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) pro parametr odpovídající argument.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="ab5a0-112">V kód volání předáte jako argument upravitelnými programovací element.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="ab5a0-113">Ve volání kódu neuvádějte argumentem v závorkách v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="ab5a0-114">V postupu kódu použijte název parametru o přiřazení hodnoty k základní elementu v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="ab5a0-115">Podívejte se na příklad další dolů pro předvedení.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="ab5a0-116">Změna místní kopie</span><span class="sxs-lookup"><span data-stu-id="ab5a0-116">Changing Local Copies</span></span>  
 <span data-ttu-id="ab5a0-117">Pokud základní element v volání kódu je neupravitelnými, nebo pokud je argument předaný `ByVal`, postup jeho hodnoty volající kód nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="ab5a0-118">Postup však můžete změnit jeho místní kopii takové argument.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="ab5a0-119">Chcete-li změnit kopii argumentu procedury v postupu kódu</span><span class="sxs-lookup"><span data-stu-id="ab5a0-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="ab5a0-120">V deklaraci postupu zadejte [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) pro parametr odpovídající argument.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="ab5a0-121">-nebo-</span><span class="sxs-lookup"><span data-stu-id="ab5a0-121">-or-</span></span>  
  
     <span data-ttu-id="ab5a0-122">Ve volání kódu uzavřete jej v závorkách v seznamu argumentů.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="ab5a0-123">Vynutí se tak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] k předání argumentu podle hodnoty, i v případě, že odpovídající parametr určuje `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-123">This forces [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="ab5a0-124">V postupu kódu použijte název parametru o přiřazení hodnoty k místní kopii argument.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="ab5a0-125">Zadaná hodnota v volání kódu se nezmění.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab5a0-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab5a0-126">Example</span></span>  
 <span data-ttu-id="ab5a0-127">Následující příklad ukazuje dva postupy, které provádějí proměnné pole a pracovat na jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="ab5a0-128">`increase` Postup jednoduše přidá jeden na každý element.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="ab5a0-129">`replace` Postup přiřadí nové pole do parametru `a()` a potom přidá jeden na každý element.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 <span data-ttu-id="ab5a0-130">První `MsgBox` volání zobrazí "po increase(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="ab5a0-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="ab5a0-131">Protože pole `n` je typu odkazu `replace` můžete změnit její členy, i když tento mechanismus předávání `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="ab5a0-132">Druhý `MsgBox` volání zobrazí "po replace(n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="ab5a0-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="ab5a0-133">Protože `n` je předán `ByRef`, `replace` můžete upravit proměnnou `n` v kódu na volání a přiřazení nové pole do ní.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="ab5a0-134">Protože `n` je typu odkazu `replace` můžete také změnit její členy.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="ab5a0-135">Můžete zabránit postup úpravy proměnné sám v volající kód.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="ab5a0-136">V tématu [postupy: ochrana argumentu procedury proti změnám hodnoty](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ab5a0-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ab5a0-137">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ab5a0-137">Compiling the Code</span></span>  
 <span data-ttu-id="ab5a0-138">Pokud předáte proměnné odkazem, je nutné použít `ByRef` – klíčové slovo zadat Tento mechanismus.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="ab5a0-139">Výchozí hodnota v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] je předání argumentů hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-139">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="ab5a0-140">Ale je dobrým zvykem obsahovat buď programovacím [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) – klíčové slovo s každou deklarovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="ab5a0-141">To výrazně zjednodušuje kódu ke čtení.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ab5a0-142">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ab5a0-142">.NET Framework Security</span></span>  
 <span data-ttu-id="ab5a0-143">Postup ke změně hodnoty základní argument volající kód, který umožňuje existuje vždy představuje potenciální riziko.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="ab5a0-144">Ujistěte se, že byste měli tuto hodnotu změnit, a zkontrolujte správnost před jeho použitím připravit.</span><span class="sxs-lookup"><span data-stu-id="ab5a0-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5a0-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab5a0-145">See Also</span></span>  
 [<span data-ttu-id="ab5a0-146">Postupy</span><span class="sxs-lookup"><span data-stu-id="ab5a0-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ab5a0-147">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="ab5a0-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ab5a0-148">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="ab5a0-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="ab5a0-149">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="ab5a0-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="ab5a0-150">Rozdíly mezi upravitelnými a Neupravitelnými argumenty</span><span class="sxs-lookup"><span data-stu-id="ab5a0-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="ab5a0-151">Rozdíly mezi předáním argumentu podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="ab5a0-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="ab5a0-152">Postupy: ochrana argumentu procedury proti změnám hodnoty</span><span class="sxs-lookup"><span data-stu-id="ab5a0-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="ab5a0-153">Postupy: vynucení předání hodnotou argumentu</span><span class="sxs-lookup"><span data-stu-id="ab5a0-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="ab5a0-154">Předávání argumentů podle pozice a názvu</span><span class="sxs-lookup"><span data-stu-id="ab5a0-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="ab5a0-155">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="ab5a0-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
