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
ms.openlocfilehash: 86758c68f0f3bfe214a695f656d3924eadd27e31
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642691"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="84849-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84849-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="84849-103">Modifikátor přístupu člena, který určuje, že jeden nebo více deklarovaný programový prvek je přístupný jenom v rámci své vlastní třídy nebo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="84849-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84849-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84849-104">Remarks</span></span>  
 <span data-ttu-id="84849-105">Někdy programovací element deklarovaný ve třídě obsahuje citlivé údaje nebo s omezeným přístupem kódu a chcete omezit přístup k elementu.</span><span class="sxs-lookup"><span data-stu-id="84849-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="84849-106">Nicméně pokud je třída odvoditelný a očekáváte, že hierarchie odvozené třídy, může být nezbytné pro tyto odvozených tříd pro přístup k data nebo kód.</span><span class="sxs-lookup"><span data-stu-id="84849-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="84849-107">V takovém případě má element být přístupné ze základní třídy a ze všech odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="84849-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="84849-108">Omezení přístupu k elementu tímto způsobem je možné deklarovat s `Protected`.</span><span class="sxs-lookup"><span data-stu-id="84849-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  

> [!NOTE]
> <span data-ttu-id="84849-109">`Protected` Modifikátor přístupu je možné kombinovat s dvěma další modifikátory:</span><span class="sxs-lookup"><span data-stu-id="84849-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
> - <span data-ttu-id="84849-110">[Protected Friend](protected-friend.md) modifikátor zpřístupňuje člen třídy z v rámci této třídy z odvozené třídy a ze stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="84849-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> 
> - <span data-ttu-id="84849-111">[Private Protected](private-protected.md) modifikátor zpřístupňuje člen třídy odvozené typy, ale pouze v rámci jeho obsahujícího sestavení.</span><span class="sxs-lookup"><span data-stu-id="84849-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>
  
## <a name="rules"></a><span data-ttu-id="84849-112">pravidla</span><span class="sxs-lookup"><span data-stu-id="84849-112">Rules</span></span>  
  
- <span data-ttu-id="84849-113">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="84849-113">**Declaration Context.**</span></span> <span data-ttu-id="84849-114">Můžete použít `Protected` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="84849-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="84849-115">To znamená, že deklarace kontext `Protected` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="84849-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  

## <a name="behavior"></a><span data-ttu-id="84849-116">Chování</span><span class="sxs-lookup"><span data-stu-id="84849-116">Behavior</span></span>  
  
- <span data-ttu-id="84849-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="84849-117">**Access Level.**</span></span> <span data-ttu-id="84849-118">Veškerý kód ve třídě můžete přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="84849-118">All code in a class can access its elements.</span></span> <span data-ttu-id="84849-119">Kód do třídy, která je odvozena ze základní třídy lze přistupovat ke všem `Protected` prvky základní třídy.</span><span class="sxs-lookup"><span data-stu-id="84849-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="84849-120">To platí pro všechny generací odvození.</span><span class="sxs-lookup"><span data-stu-id="84849-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="84849-121">To znamená, že se třída dostanete `Protected` elementů základní třídy základní třídy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="84849-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="84849-122">Chráněného přístupu je nadmnožinou nebo podmnožinu přístup typu friend.</span><span class="sxs-lookup"><span data-stu-id="84849-122">Protected access is not a superset or subset of friend access.</span></span>  
  
- <span data-ttu-id="84849-123">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="84849-123">**Access Modifiers.**</span></span> <span data-ttu-id="84849-124">Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="84849-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="84849-125">Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="84849-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="84849-126">`Protected` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="84849-126">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="84849-127">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="84849-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="84849-128">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="84849-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="84849-129">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="84849-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="84849-130">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="84849-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="84849-131">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="84849-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="84849-132">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="84849-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="84849-133">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="84849-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="84849-134">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="84849-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="84849-135">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="84849-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="84849-136">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="84849-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="84849-137">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="84849-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="84849-138">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="84849-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="84849-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84849-139">See also</span></span>

- [<span data-ttu-id="84849-140">Public</span><span class="sxs-lookup"><span data-stu-id="84849-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="84849-141">Friend</span><span class="sxs-lookup"><span data-stu-id="84849-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="84849-142">Private</span><span class="sxs-lookup"><span data-stu-id="84849-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="84849-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="84849-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="84849-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="84849-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="84849-145">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84849-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="84849-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="84849-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="84849-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="84849-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="84849-148">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="84849-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
