---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235915"
---
# <a name="public-visual-basic"></a><span data-ttu-id="3ef45-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ef45-102">Public (Visual Basic)</span></span>
<span data-ttu-id="3ef45-103">Určuje, že jeden nebo více deklarované programovací elementy žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="3ef45-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ef45-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ef45-104">Remarks</span></span>  
 <span data-ttu-id="3ef45-105">Při publikování komponenty nebo sadu součástí, například knihovny tříd, chcete obvykle programovací prvky, které mají být přístupné kód, který bude spolupracovat s vaší sestavení.</span><span class="sxs-lookup"><span data-stu-id="3ef45-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="3ef45-106">Přenést takové neomezený přístup na element, můžou deklarovat její `Public`.</span><span class="sxs-lookup"><span data-stu-id="3ef45-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="3ef45-107">Veřejný přístup je úroveň programovací element v normální, pokud nepotřebujete omezit přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="3ef45-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="3ef45-108">Všimněte si, že úroveň přístupu tohoto elementu deklarované v rámci rozhraní, modulu, třídu nebo strukturu výchozí `Public` Pokud neprovedete deklaraci ho jinak.</span><span class="sxs-lookup"><span data-stu-id="3ef45-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3ef45-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="3ef45-109">Rules</span></span>  
  
-   <span data-ttu-id="3ef45-110">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="3ef45-110">**Declaration Context.**</span></span> <span data-ttu-id="3ef45-111">Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="3ef45-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="3ef45-112">To znamená kontext deklarace `Public` element musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídu nebo strukturu a nemůže být procedury.</span><span class="sxs-lookup"><span data-stu-id="3ef45-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3ef45-113">Chování</span><span class="sxs-lookup"><span data-stu-id="3ef45-113">Behavior</span></span>  
  
-   <span data-ttu-id="3ef45-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="3ef45-114">**Access Level.**</span></span> <span data-ttu-id="3ef45-115">Všechny kód, který můžete získat přístup k modulu, třídu nebo strukturu můžete přístup k jeho `Public` elementy.</span><span class="sxs-lookup"><span data-stu-id="3ef45-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="3ef45-116">**Výchozí úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="3ef45-116">**Default Access.**</span></span> <span data-ttu-id="3ef45-117">Lokální proměnné uvnitř procedury výchozí veřejný přístup, a nelze použít žádné modifikátory přístupu na ně.</span><span class="sxs-lookup"><span data-stu-id="3ef45-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="3ef45-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="3ef45-118">**Access Modifiers.**</span></span> <span data-ttu-id="3ef45-119">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="3ef45-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="3ef45-120">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3ef45-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="3ef45-121">`Public` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="3ef45-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3ef45-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="3ef45-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="3ef45-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="3ef45-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="3ef45-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="3ef45-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="3ef45-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="3ef45-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="3ef45-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="3ef45-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="3ef45-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="3ef45-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="3ef45-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="3ef45-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="3ef45-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="3ef45-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="3ef45-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="3ef45-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="3ef45-131">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="3ef45-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="3ef45-132">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="3ef45-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="3ef45-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="3ef45-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="3ef45-134">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="3ef45-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="3ef45-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="3ef45-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ef45-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ef45-136">See Also</span></span>  
 [<span data-ttu-id="3ef45-137">Protected</span><span class="sxs-lookup"><span data-stu-id="3ef45-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="3ef45-138">Friend</span><span class="sxs-lookup"><span data-stu-id="3ef45-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="3ef45-139">Private</span><span class="sxs-lookup"><span data-stu-id="3ef45-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="3ef45-140">[Privátní chráněný](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="3ef45-140">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="3ef45-141">[Chráněné Friend](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="3ef45-141">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="3ef45-142">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3ef45-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="3ef45-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="3ef45-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="3ef45-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="3ef45-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="3ef45-145">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="3ef45-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
