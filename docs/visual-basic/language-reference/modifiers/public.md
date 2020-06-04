---
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415346"
---
# <a name="public-visual-basic"></a><span data-ttu-id="3d6c7-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3d6c7-102">Public (Visual Basic)</span></span>
<span data-ttu-id="3d6c7-103">Určuje, že nejmíň jeden deklarovaný programový prvek nemá žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d6c7-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d6c7-104">Remarks</span></span>  
 <span data-ttu-id="3d6c7-105">Pokud publikujete součást nebo sadu komponent, jako je například knihovna tříd, obvykle chcete, aby byly k dispozici programové prvky pro jakýkoliv kód, který spolupracuje s vaším sestavením.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="3d6c7-106">Chcete-li udělit takovému neomezenému přístupu u prvku, můžete ho deklarovat pomocí `Public` .</span><span class="sxs-lookup"><span data-stu-id="3d6c7-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="3d6c7-107">Veřejný přístup je normální úroveň pro programovací prvek, pokud nepotřebujete omezit přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="3d6c7-108">Všimněte si, že úroveň přístupu elementu deklarovaného v rámci výchozího rozhraní, modulu, třídy nebo struktury je v `Public` případě, že jej nedeklarujete jinak.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3d6c7-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="3d6c7-109">Rules</span></span>  
  
- <span data-ttu-id="3d6c7-110">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="3d6c7-110">**Declaration Context.**</span></span> <span data-ttu-id="3d6c7-111">Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="3d6c7-112">To znamená, že kontext deklarace pro `Public` prvek musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura a nemůže být procedura.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3d6c7-113">Chování</span><span class="sxs-lookup"><span data-stu-id="3d6c7-113">Behavior</span></span>  
  
- <span data-ttu-id="3d6c7-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="3d6c7-114">**Access Level.**</span></span> <span data-ttu-id="3d6c7-115">Veškerý kód, který má přístup k modulu, třídě nebo struktuře, má přístup k jeho `Public` prvkům.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="3d6c7-116">**Výchozí přístup**</span><span class="sxs-lookup"><span data-stu-id="3d6c7-116">**Default Access.**</span></span> <span data-ttu-id="3d6c7-117">Místní proměnné uvnitř procedury jsou ve výchozím nastavení veřejný přístup a nemůžete použít žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="3d6c7-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="3d6c7-118">**Access Modifiers.**</span></span> <span data-ttu-id="3d6c7-119">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="3d6c7-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="3d6c7-120">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3d6c7-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="3d6c7-121">`Public`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="3d6c7-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="3d6c7-122">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-122">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="3d6c7-123">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-123">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="3d6c7-124">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-124">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="3d6c7-125">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-125">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="3d6c7-126">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-126">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="3d6c7-127">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-127">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="3d6c7-128">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-128">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="3d6c7-129">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-129">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="3d6c7-130">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-130">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="3d6c7-131">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-131">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="3d6c7-132">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-132">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 [<span data-ttu-id="3d6c7-133">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-133">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="3d6c7-134">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-134">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="3d6c7-135">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="3d6c7-135">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3d6c7-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d6c7-136">See also</span></span>

- [<span data-ttu-id="3d6c7-137">Proti</span><span class="sxs-lookup"><span data-stu-id="3d6c7-137">Protected</span></span>](protected.md)
- [<span data-ttu-id="3d6c7-138">Friend</span><span class="sxs-lookup"><span data-stu-id="3d6c7-138">Friend</span></span>](friend.md)
- [<span data-ttu-id="3d6c7-139">Hlášen</span><span class="sxs-lookup"><span data-stu-id="3d6c7-139">Private</span></span>](private.md)
- [<span data-ttu-id="3d6c7-140">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="3d6c7-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="3d6c7-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="3d6c7-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="3d6c7-142">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3d6c7-142">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="3d6c7-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="3d6c7-143">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="3d6c7-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="3d6c7-144">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="3d6c7-145">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="3d6c7-145">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
