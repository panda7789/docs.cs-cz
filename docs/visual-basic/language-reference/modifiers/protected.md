---
title: Chráněno
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
ms.openlocfilehash: 740c998b8a6ccc6798bce37e9b08e408dac7c17d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351306"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="b9ef1-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b9ef1-102">Protected (Visual Basic)</span></span>

<span data-ttu-id="b9ef1-103">Modifikátor přístupu ke členu, který určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci své vlastní třídy nebo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="b9ef1-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9ef1-104">Remarks</span></span>

<span data-ttu-id="b9ef1-105">V některých případech programovací element deklarovaný ve třídě obsahuje citlivá data nebo omezený kód a vy chcete omezit přístup k elementu.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="b9ef1-106">Nicméně, pokud je třída děděna a očekáváte hierarchii odvozených tříd, může být nutné, aby tyto odvozené třídy měly přístup k datům nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="b9ef1-107">V takovém případě chcete, aby byl prvek přístupný jak ze základní třídy, tak ze všech odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="b9ef1-108">Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Protected`.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="b9ef1-109">Modifikátor přístupu `Protected` lze kombinovat se dvěma dalšími modifikátory:</span><span class="sxs-lookup"><span data-stu-id="b9ef1-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="b9ef1-110">[Chráněný modifikátor Friend](protected-friend.md) zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="b9ef1-111">Modifikátor [Private protecter](private-protected.md) zpřístupňuje člena třídy, který je přístupný odvozeným typům, ale pouze v rámci jeho nadřazeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="b9ef1-112">Pravidla</span><span class="sxs-lookup"><span data-stu-id="b9ef1-112">Rules</span></span>

<span data-ttu-id="b9ef1-113">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="b9ef1-113">**Declaration Context.**</span></span> <span data-ttu-id="b9ef1-114">`Protected` lze použít pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="b9ef1-115">To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="b9ef1-116">Chování</span><span class="sxs-lookup"><span data-stu-id="b9ef1-116">Behavior</span></span>

- <span data-ttu-id="b9ef1-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="b9ef1-117">**Access Level.**</span></span> <span data-ttu-id="b9ef1-118">Veškerý kód ve třídě má přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-118">All code in a class can access its elements.</span></span> <span data-ttu-id="b9ef1-119">Kód v jakékoli třídě, která je odvozena od základní třídy, má přístup ke všem prvkům `Protected` základní třídy.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="b9ef1-120">To platí pro všechny generace odvození.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="b9ef1-121">To znamená, že třída může přistupovat k prvkům `Protected` základní třídy základní třídy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="b9ef1-122">Protected Access není nadmnožinou ani podmnožinou přístupu typu Friend.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-122">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="b9ef1-123">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="b9ef1-123">**Access Modifiers.**</span></span> <span data-ttu-id="b9ef1-124">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="b9ef1-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="b9ef1-125">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b9ef1-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="b9ef1-126">V těchto kontextech lze použít modifikátor `Protected`:</span><span class="sxs-lookup"><span data-stu-id="b9ef1-126">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="b9ef1-127">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="b9ef1-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="b9ef1-128">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="b9ef1-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="b9ef1-129">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="b9ef1-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="b9ef1-130">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="b9ef1-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="b9ef1-131">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="b9ef1-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="b9ef1-132">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="b9ef1-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="b9ef1-133">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="b9ef1-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="b9ef1-134">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="b9ef1-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="b9ef1-135">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="b9ef1-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="b9ef1-136">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="b9ef1-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="b9ef1-137">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="b9ef1-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="b9ef1-138">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="b9ef1-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="b9ef1-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9ef1-139">See also</span></span>

- [<span data-ttu-id="b9ef1-140">Public</span><span class="sxs-lookup"><span data-stu-id="b9ef1-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="b9ef1-141">Friend</span><span class="sxs-lookup"><span data-stu-id="b9ef1-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="b9ef1-142">Private</span><span class="sxs-lookup"><span data-stu-id="b9ef1-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="b9ef1-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="b9ef1-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="b9ef1-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="b9ef1-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="b9ef1-145">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9ef1-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="b9ef1-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="b9ef1-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="b9ef1-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="b9ef1-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="b9ef1-148">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="b9ef1-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
