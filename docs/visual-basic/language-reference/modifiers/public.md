---
title: Public (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6cd70adf6ec31c56f39d0443d320dd1b00b00d3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="public-visual-basic"></a><span data-ttu-id="9b0e7-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9b0e7-102">Public (Visual Basic)</span></span>
<span data-ttu-id="9b0e7-103">Určuje, že jeden nebo více deklarované programovací elementy žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b0e7-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b0e7-104">Remarks</span></span>  
 <span data-ttu-id="9b0e7-105">Při publikování komponenty nebo sadu součástí, například knihovny tříd, chcete obvykle programovací prvky, které mají být přístupné kód, který bude spolupracovat s vaší sestavení.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="9b0e7-106">Přenést takové neomezený přístup na element, můžou deklarovat její `Public`.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="9b0e7-107">Veřejný přístup je úroveň programovací element v normální, pokud nepotřebujete omezit přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="9b0e7-108">Všimněte si, že úroveň přístupu tohoto elementu deklarované v rámci rozhraní, modulu, třídu nebo strukturu výchozí `Public` Pokud neprovedete deklaraci ho jinak.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9b0e7-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="9b0e7-109">Rules</span></span>  
  
-   <span data-ttu-id="9b0e7-110">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-110">**Declaration Context.**</span></span> <span data-ttu-id="9b0e7-111">Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="9b0e7-112">To znamená kontext deklarace `Public` element musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídu nebo strukturu a nemůže být procedury.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="9b0e7-113">Chování</span><span class="sxs-lookup"><span data-stu-id="9b0e7-113">Behavior</span></span>  
  
-   <span data-ttu-id="9b0e7-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-114">**Access Level.**</span></span> <span data-ttu-id="9b0e7-115">Všechny kód, který můžete získat přístup k modulu, třídu nebo strukturu můžete přístup k jeho `Public` elementy.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="9b0e7-116">**Výchozí úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-116">**Default Access.**</span></span> <span data-ttu-id="9b0e7-117">Lokální proměnné uvnitř procedury výchozí veřejný přístup, a nelze použít žádné modifikátory přístupu na ně.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="9b0e7-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="9b0e7-118">**Access Modifiers.**</span></span> <span data-ttu-id="9b0e7-119">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="9b0e7-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="9b0e7-120">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="9b0e7-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="9b0e7-121">`Public` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="9b0e7-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="9b0e7-122">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="9b0e7-123">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="9b0e7-124">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="9b0e7-125">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="9b0e7-126">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="9b0e7-127">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="9b0e7-128">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="9b0e7-129">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="9b0e7-130">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="9b0e7-131">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="9b0e7-132">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="9b0e7-133">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="9b0e7-134">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="9b0e7-135">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="9b0e7-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b0e7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b0e7-136">See Also</span></span>  
 [<span data-ttu-id="9b0e7-137">Chráněný</span><span class="sxs-lookup"><span data-stu-id="9b0e7-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="9b0e7-138">Friend</span><span class="sxs-lookup"><span data-stu-id="9b0e7-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="9b0e7-139">Privátní</span><span class="sxs-lookup"><span data-stu-id="9b0e7-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="9b0e7-140">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9b0e7-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="9b0e7-141">Postupy</span><span class="sxs-lookup"><span data-stu-id="9b0e7-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="9b0e7-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="9b0e7-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="9b0e7-143">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="9b0e7-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
