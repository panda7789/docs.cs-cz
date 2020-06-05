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
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398217"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="2fb5a-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fb5a-102">Protected (Visual Basic)</span></span>

<span data-ttu-id="2fb5a-103">Modifikátor přístupu ke členu, který určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci své vlastní třídy nebo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fb5a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2fb5a-104">Remarks</span></span>

<span data-ttu-id="2fb5a-105">V některých případech programovací element deklarovaný ve třídě obsahuje citlivá data nebo omezený kód a vy chcete omezit přístup k elementu.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="2fb5a-106">Nicméně, pokud je třída děděna a očekáváte hierarchii odvozených tříd, může být nutné, aby tyto odvozené třídy měly přístup k datům nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="2fb5a-107">V takovém případě chcete, aby byl prvek přístupný jak ze základní třídy, tak ze všech odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="2fb5a-108">Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Protected` .</span><span class="sxs-lookup"><span data-stu-id="2fb5a-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="2fb5a-109">`Protected`Modifikátor přístupu lze kombinovat se dvěma dalšími modifikátory:</span><span class="sxs-lookup"><span data-stu-id="2fb5a-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="2fb5a-110">[Chráněný modifikátor Friend](protected-friend.md) zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="2fb5a-111">Modifikátor [Private protecter](private-protected.md) zpřístupňuje člena třídy, který je přístupný odvozeným typům, ale pouze v rámci jeho nadřazeného sestavení.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="2fb5a-112">Pravidla</span><span class="sxs-lookup"><span data-stu-id="2fb5a-112">Rules</span></span>

<span data-ttu-id="2fb5a-113">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="2fb5a-113">**Declaration Context.**</span></span> <span data-ttu-id="2fb5a-114">Můžete použít `Protected` pouze na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="2fb5a-115">To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="2fb5a-116">Chování</span><span class="sxs-lookup"><span data-stu-id="2fb5a-116">Behavior</span></span>

- <span data-ttu-id="2fb5a-117">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="2fb5a-117">**Access Level.**</span></span> <span data-ttu-id="2fb5a-118">Veškerý kód ve třídě má přístup k jeho prvkům.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-118">All code in a class can access its elements.</span></span> <span data-ttu-id="2fb5a-119">Kód v jakékoli třídě, která je odvozena od základní třídy, má přístup ke všem `Protected` prvkům základní třídy.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="2fb5a-120">To platí pro všechny generace odvození.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="2fb5a-121">To znamená, že třída může přistupovat k `Protected` prvkům základní třídy základní třídy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="2fb5a-122">Protected Access není nadmnožinou ani podmnožinou přístupu typu Friend.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-122">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="2fb5a-123">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="2fb5a-123">**Access Modifiers.**</span></span> <span data-ttu-id="2fb5a-124">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="2fb5a-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2fb5a-125">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2fb5a-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="2fb5a-126">`Protected`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="2fb5a-126">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="2fb5a-127">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-127">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="2fb5a-128">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-128">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="2fb5a-129">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-129">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="2fb5a-130">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-130">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="2fb5a-131">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-131">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="2fb5a-132">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-132">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="2fb5a-133">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-133">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="2fb5a-134">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-134">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="2fb5a-135">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-135">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="2fb5a-136">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-136">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="2fb5a-137">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-137">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="2fb5a-138">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="2fb5a-138">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="2fb5a-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fb5a-139">See also</span></span>

- [<span data-ttu-id="2fb5a-140">Republik</span><span class="sxs-lookup"><span data-stu-id="2fb5a-140">Public</span></span>](public.md)
- [<span data-ttu-id="2fb5a-141">Friend</span><span class="sxs-lookup"><span data-stu-id="2fb5a-141">Friend</span></span>](friend.md)
- [<span data-ttu-id="2fb5a-142">Hlášen</span><span class="sxs-lookup"><span data-stu-id="2fb5a-142">Private</span></span>](private.md)
- [<span data-ttu-id="2fb5a-143">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="2fb5a-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="2fb5a-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="2fb5a-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="2fb5a-145">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fb5a-145">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2fb5a-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="2fb5a-146">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2fb5a-147">Struktury</span><span class="sxs-lookup"><span data-stu-id="2fb5a-147">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2fb5a-148">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="2fb5a-148">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
