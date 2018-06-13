---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 5f279ed0a33840bb1f2321c17a1ffba412837c07
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234754"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="30e47-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30e47-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="30e47-103">Člen – modifikátor přístupu, která určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v rámci své vlastní třídy nebo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="30e47-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30e47-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30e47-104">Remarks</span></span>  
 <span data-ttu-id="30e47-105">Někdy programovací element deklarovaná ve třídě obsahuje citlivá data nebo kód s omezeným přístupem, a chcete omezit přístup k elementu.</span><span class="sxs-lookup"><span data-stu-id="30e47-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="30e47-106">Ale pokud ze třídy a očekáváte, že hierarchie odvozených tříd, může být nezbytné pro tyto odvozené třídy přistupovat k datům nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="30e47-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="30e47-107">V takovém případě budete chtít elementu, který chcete být přístupné ze základní třídy a z všechny odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="30e47-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="30e47-108">Omezit přístup k elementu tímto způsobem, můžou deklarovat její `Protected`.</span><span class="sxs-lookup"><span data-stu-id="30e47-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="30e47-109">`Protected` – Modifikátor přístupu je možné kombinovat s dva další modifikátory:</span><span class="sxs-lookup"><span data-stu-id="30e47-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="30e47-110">[Protected Friend](protected-friend.md) modifikátor zpřístupní člena třídy z v rámci třídy, v rámci odvozené třídy a do stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="30e47-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="30e47-111">[Privátní chráněné](private-protected.md) modifikátor zpřístupní člena třídy odvozené typy, ale jenom v rámci jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="30e47-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="30e47-112">Pravidla</span><span class="sxs-lookup"><span data-stu-id="30e47-112">Rules</span></span>  
  
-   <span data-ttu-id="30e47-113">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="30e47-113">**Declaration Context.**</span></span> <span data-ttu-id="30e47-114">Můžete použít `Protected` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="30e47-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="30e47-115">To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.</span><span class="sxs-lookup"><span data-stu-id="30e47-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="30e47-116">Chování</span><span class="sxs-lookup"><span data-stu-id="30e47-116">Behavior</span></span>  
  
-   <span data-ttu-id="30e47-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="30e47-117">**Access Level.**</span></span> <span data-ttu-id="30e47-118">Všechny kódu v třídě mají přístup k jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="30e47-118">All code in a class can access its elements.</span></span> <span data-ttu-id="30e47-119">Kód do třídy, která je odvozena ze základní třídy mají přístup ke všem `Protected` elementy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="30e47-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="30e47-120">To platí pro všechny generací odvození.</span><span class="sxs-lookup"><span data-stu-id="30e47-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="30e47-121">To znamená, že třídu přístup `Protected` elementy základní třídy základní třídy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="30e47-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="30e47-122">Chráněného přístupu není nadmnožinou nebo podmnožinu friend přístup.</span><span class="sxs-lookup"><span data-stu-id="30e47-122">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="30e47-123">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="30e47-123">**Access Modifiers.**</span></span> <span data-ttu-id="30e47-124">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="30e47-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="30e47-125">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="30e47-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="30e47-126">`Protected` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="30e47-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="30e47-127">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="30e47-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="30e47-128">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="30e47-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="30e47-129">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="30e47-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="30e47-130">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="30e47-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="30e47-131">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="30e47-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="30e47-132">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="30e47-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="30e47-133">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="30e47-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="30e47-134">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="30e47-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="30e47-135">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="30e47-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="30e47-136">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="30e47-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="30e47-137">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="30e47-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="30e47-138">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="30e47-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="30e47-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="30e47-139">See Also</span></span>  
 [<span data-ttu-id="30e47-140">Public</span><span class="sxs-lookup"><span data-stu-id="30e47-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="30e47-141">Friend</span><span class="sxs-lookup"><span data-stu-id="30e47-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="30e47-142">Private</span><span class="sxs-lookup"><span data-stu-id="30e47-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="30e47-143">[Privátní chráněný](private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="30e47-143">[Private Protected](private-protected.md) </span></span>  
 <span data-ttu-id="30e47-144">[Chráněné Friend](protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="30e47-144">[Protected Friend](protected-friend.md) </span></span>  
 [<span data-ttu-id="30e47-145">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30e47-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="30e47-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="30e47-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="30e47-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="30e47-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="30e47-148">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="30e47-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
