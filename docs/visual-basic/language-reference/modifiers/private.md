---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234552"
---
# <a name="private-visual-basic"></a><span data-ttu-id="979a7-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="979a7-102">Private (Visual Basic)</span></span>
<span data-ttu-id="979a7-103">Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v kontextu jejich deklarace, včetně v rámci všechny obsažené typy.</span><span class="sxs-lookup"><span data-stu-id="979a7-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="979a7-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="979a7-104">Remarks</span></span>  
 <span data-ttu-id="979a7-105">Pokud programovací element představuje speciálních funkcí, nebo obsahuje důvěrných dat, obvykle chcete omezit přístup k němu jako výhradně.</span><span class="sxs-lookup"><span data-stu-id="979a7-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="979a7-106">Maximální omezení můžete dosáhnout tím, že pouze modulu, třídu nebo strukturu, která definuje, aby k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="979a7-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="979a7-107">Omezit přístup k elementu tímto způsobem, můžou deklarovat její `Private`.</span><span class="sxs-lookup"><span data-stu-id="979a7-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="979a7-108">Můžete také [privátní chráněné](private-protected.md) – modifikátor přístupu, které umožňuje členem přístup z v rámci třídy a z odvozené třídy, které jsou umístěné v jeho obsahující sestavení.</span><span class="sxs-lookup"><span data-stu-id="979a7-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="979a7-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="979a7-109">Rules</span></span>  

-   <span data-ttu-id="979a7-110">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="979a7-110">**Declaration Context.**</span></span> <span data-ttu-id="979a7-111">Můžete použít `Private` jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="979a7-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="979a7-112">To znamená kontext deklarace `Private` element musí být modul, třídu nebo strukturu a nemůže být zdrojový soubor, obor názvů, rozhraní nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="979a7-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="979a7-113">Chování</span><span class="sxs-lookup"><span data-stu-id="979a7-113">Behavior</span></span>  
  
-   <span data-ttu-id="979a7-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="979a7-114">**Access Level.**</span></span> <span data-ttu-id="979a7-115">Všechny kódu v rámci kontextu deklarace můžete přístup k jeho `Private` elementy.</span><span class="sxs-lookup"><span data-stu-id="979a7-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="979a7-116">To zahrnuje kódu v rámci omezením typu, například vnořené třídy nebo výraz přiřazení ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="979a7-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="979a7-117">Žádný kód mimo kontext deklarace můžete přístup k jeho `Private` elementy.</span><span class="sxs-lookup"><span data-stu-id="979a7-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="979a7-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="979a7-118">**Access Modifiers.**</span></span> <span data-ttu-id="979a7-119">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="979a7-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="979a7-120">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="979a7-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="979a7-121">`Private` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="979a7-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="979a7-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="979a7-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="979a7-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="979a7-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="979a7-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="979a7-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="979a7-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="979a7-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="979a7-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="979a7-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="979a7-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="979a7-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="979a7-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="979a7-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="979a7-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="979a7-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="979a7-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="979a7-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="979a7-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="979a7-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="979a7-132">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="979a7-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="979a7-133">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="979a7-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="979a7-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="979a7-134">See Also</span></span>  
 [<span data-ttu-id="979a7-135">Public</span><span class="sxs-lookup"><span data-stu-id="979a7-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="979a7-136">Protected</span><span class="sxs-lookup"><span data-stu-id="979a7-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="979a7-137">Friend</span><span class="sxs-lookup"><span data-stu-id="979a7-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 <span data-ttu-id="979a7-138">[Privátní chráněný](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="979a7-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="979a7-139">[Protected Friend](./protected-friend.md)[přístup úrovně v jazyce Visual Basic    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="979a7-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>  
 [<span data-ttu-id="979a7-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="979a7-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="979a7-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="979a7-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="979a7-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="979a7-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
