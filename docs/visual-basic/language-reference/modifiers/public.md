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
ms.openlocfilehash: 0c85564503f3c83e436044cd92ee3014945f1ef3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818381"
---
# <a name="public-visual-basic"></a><span data-ttu-id="53979-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53979-102">Public (Visual Basic)</span></span>
<span data-ttu-id="53979-103">Určuje, že nejmíň jeden deklarovaný programový prvek nemá žádné omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="53979-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53979-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53979-104">Remarks</span></span>  
 <span data-ttu-id="53979-105">Pokud publikujete komponenta nebo sadu komponent, jako je například knihovny tříd, obvykle vhodné programovací prvky, které mají být přístupné pro jakýkoli kód, který spolupracuje s vaší sestavení.</span><span class="sxs-lookup"><span data-stu-id="53979-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="53979-106">Přenést taková neomezený přístup elementu, je možné deklarovat s `Public`.</span><span class="sxs-lookup"><span data-stu-id="53979-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="53979-107">Veřejný přístup je normální úroveň pro programovací prvek, pokud nepotřebujete omezit přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="53979-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="53979-108">Všimněte si, že úroveň přístupu elementu deklarované v rámci rozhraní, modulu, třídy nebo struktury výchozí hodnota je `Public` je-li ho jinak není deklarována.</span><span class="sxs-lookup"><span data-stu-id="53979-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="53979-109">pravidla</span><span class="sxs-lookup"><span data-stu-id="53979-109">Rules</span></span>  
  
-   <span data-ttu-id="53979-110">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="53979-110">**Declaration Context.**</span></span> <span data-ttu-id="53979-111">Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="53979-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="53979-112">To znamená, že deklarace kontext `Public` elementu musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídy nebo struktury a nemůže být procedurou.</span><span class="sxs-lookup"><span data-stu-id="53979-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="53979-113">Chování</span><span class="sxs-lookup"><span data-stu-id="53979-113">Behavior</span></span>  
  
-   <span data-ttu-id="53979-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="53979-114">**Access Level.**</span></span> <span data-ttu-id="53979-115">Veškerý kód, který může přistupovat k modulu, třídy nebo struktury lze přistupovat k jeho `Public` elementy.</span><span class="sxs-lookup"><span data-stu-id="53979-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
-   <span data-ttu-id="53979-116">**Výchozí přístup.**</span><span class="sxs-lookup"><span data-stu-id="53979-116">**Default Access.**</span></span> <span data-ttu-id="53979-117">Místní proměnná uvnitř procedury výchozí veřejný přístup, a nemůže používat žádné modifikátory přístupu na nich.</span><span class="sxs-lookup"><span data-stu-id="53979-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
-   <span data-ttu-id="53979-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="53979-118">**Access Modifiers.**</span></span> <span data-ttu-id="53979-119">Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*.</span><span class="sxs-lookup"><span data-stu-id="53979-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="53979-120">Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="53979-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="53979-121">`Public` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="53979-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="53979-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="53979-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="53979-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="53979-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="53979-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="53979-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="53979-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="53979-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="53979-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="53979-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="53979-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="53979-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="53979-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="53979-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="53979-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="53979-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="53979-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="53979-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="53979-131">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="53979-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="53979-132">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="53979-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="53979-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="53979-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="53979-134">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="53979-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="53979-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="53979-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="53979-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53979-136">See also</span></span>

- [<span data-ttu-id="53979-137">Protected</span><span class="sxs-lookup"><span data-stu-id="53979-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="53979-138">Friend</span><span class="sxs-lookup"><span data-stu-id="53979-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="53979-139">Private</span><span class="sxs-lookup"><span data-stu-id="53979-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="53979-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="53979-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="53979-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="53979-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="53979-142">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53979-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="53979-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="53979-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="53979-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="53979-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="53979-145">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="53979-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
