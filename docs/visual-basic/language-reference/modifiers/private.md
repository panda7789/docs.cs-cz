---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819473"
---
# <a name="private-visual-basic"></a><span data-ttu-id="94ff1-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94ff1-102">Private (Visual Basic)</span></span>
<span data-ttu-id="94ff1-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci kontextu jejich prohlášení, včetně z v rámci žádné typy obsažené.</span><span class="sxs-lookup"><span data-stu-id="94ff1-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94ff1-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94ff1-104">Remarks</span></span>  
 <span data-ttu-id="94ff1-105">Pokud programovací element představuje speciálních funkcí, nebo obsahuje důvěrná data, obvykle chcete omezit přístup k němu jako přísně.</span><span class="sxs-lookup"><span data-stu-id="94ff1-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="94ff1-106">Dosažení maximálního omezení tím, že pouze modul, třídu nebo strukturu, která definuje se k němu přistupovat.</span><span class="sxs-lookup"><span data-stu-id="94ff1-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="94ff1-107">Omezení přístupu k elementu tímto způsobem je možné deklarovat s `Private`.</span><span class="sxs-lookup"><span data-stu-id="94ff1-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="94ff1-108">Můžete také použít [Private Protected](private-protected.md) modifikátor přístupu, který zpřístupňuje člen z v rámci třídy a z odvozených tříd, které jsou umístěné v jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="94ff1-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="94ff1-109">pravidla</span><span class="sxs-lookup"><span data-stu-id="94ff1-109">Rules</span></span>  

-   <span data-ttu-id="94ff1-110">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="94ff1-110">**Declaration Context.**</span></span> <span data-ttu-id="94ff1-111">Můžete použít `Private` pouze na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="94ff1-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="94ff1-112">To znamená, že deklarace kontext `Private` elementu musí být modulu, třídy nebo struktury a nemůže být zdrojový soubor, obor názvů, rozhraní nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="94ff1-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="94ff1-113">Chování</span><span class="sxs-lookup"><span data-stu-id="94ff1-113">Behavior</span></span>  
  
-   <span data-ttu-id="94ff1-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="94ff1-114">**Access Level.**</span></span> <span data-ttu-id="94ff1-115">Veškerý kód v rámci kontextu deklarace můžete přístup k jeho `Private` elementy.</span><span class="sxs-lookup"><span data-stu-id="94ff1-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="94ff1-116">To zahrnuje kód v rámci omezením typu, jako je vnořená třída nebo výrazu přiřazení ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="94ff1-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="94ff1-117">Žádný kód mimo kontext deklarace můžete získat přístup k jeho `Private` elementy.</span><span class="sxs-lookup"><span data-stu-id="94ff1-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="94ff1-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="94ff1-118">**Access Modifiers.**</span></span> <span data-ttu-id="94ff1-119">Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="94ff1-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="94ff1-120">Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="94ff1-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="94ff1-121">`Private` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="94ff1-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="94ff1-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="94ff1-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="94ff1-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="94ff1-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="94ff1-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="94ff1-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="94ff1-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="94ff1-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="94ff1-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="94ff1-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="94ff1-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="94ff1-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="94ff1-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="94ff1-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="94ff1-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="94ff1-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="94ff1-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="94ff1-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="94ff1-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="94ff1-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="94ff1-132">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="94ff1-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="94ff1-133">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="94ff1-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="94ff1-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94ff1-134">See also</span></span>

- [<span data-ttu-id="94ff1-135">Public</span><span class="sxs-lookup"><span data-stu-id="94ff1-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="94ff1-136">Protected</span><span class="sxs-lookup"><span data-stu-id="94ff1-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="94ff1-137">Friend</span><span class="sxs-lookup"><span data-stu-id="94ff1-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="94ff1-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="94ff1-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="94ff1-139">[Protected Friend](./protected-friend.md)[přístup úrovně v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="94ff1-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="94ff1-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="94ff1-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="94ff1-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="94ff1-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="94ff1-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="94ff1-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
