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
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351297"
---
# <a name="public-visual-basic"></a><span data-ttu-id="2b4c0-102">Public (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b4c0-102">Public (Visual Basic)</span></span>
<span data-ttu-id="2b4c0-103">Určuje, že nejmíň jeden deklarovaný programový prvek nemá žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-103">Specifies that one or more declared programming elements have no access restrictions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b4c0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b4c0-104">Remarks</span></span>  
 <span data-ttu-id="2b4c0-105">Pokud publikujete součást nebo sadu komponent, jako je například knihovna tříd, obvykle chcete, aby byly k dispozici programové prvky pro jakýkoliv kód, který spolupracuje s vaším sestavením.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-105">If you are publishing a component or set of components, such as a class library, you usually want the programming elements to be accessible by any code that interoperates with your assembly.</span></span> <span data-ttu-id="2b4c0-106">Chcete-li udělit takovému neomezenému přístupu u prvku, můžete ho deklarovat pomocí `Public`.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-106">To confer such unlimited access on an element, you can declare it with `Public`.</span></span>  
  
 <span data-ttu-id="2b4c0-107">Veřejný přístup je normální úroveň pro programovací prvek, pokud nepotřebujete omezit přístup k němu.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-107">Public access is the normal level for a programming element when you do not need to limit access to it.</span></span> <span data-ttu-id="2b4c0-108">Všimněte si, že úroveň přístupu elementu deklarovaného v rámci rozhraní, modulu, třídy nebo struktury se standardně `Public`, pokud jej nedeklarujete jinak.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-108">Note that the access level of an element declared within an interface, module, class, or structure defaults to `Public` if you do not declare it otherwise.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2b4c0-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="2b4c0-109">Rules</span></span>  
  
- <span data-ttu-id="2b4c0-110">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="2b4c0-110">**Declaration Context.**</span></span> <span data-ttu-id="2b4c0-111">`Public` lze použít pouze na úrovni modulu, rozhraní nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-111">You can use `Public` only at module, interface, or namespace level.</span></span> <span data-ttu-id="2b4c0-112">To znamená, že kontext deklarace pro prvek `Public` musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura a nemůže být procedura.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-112">This means the declaration context for a `Public` element must be a source file, namespace, interface, module, class, or structure, and cannot be a procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2b4c0-113">Chování</span><span class="sxs-lookup"><span data-stu-id="2b4c0-113">Behavior</span></span>  
  
- <span data-ttu-id="2b4c0-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="2b4c0-114">**Access Level.**</span></span> <span data-ttu-id="2b4c0-115">Veškerý kód, který má přístup k modulu, třídě nebo struktuře, má přístup k jeho prvkům `Public`.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-115">All code that can access a module, class, or structure can access its `Public` elements.</span></span>  
  
- <span data-ttu-id="2b4c0-116">**Výchozí přístup**</span><span class="sxs-lookup"><span data-stu-id="2b4c0-116">**Default Access.**</span></span> <span data-ttu-id="2b4c0-117">Místní proměnné uvnitř procedury jsou ve výchozím nastavení veřejný přístup a nemůžete použít žádné modifikátory přístupu.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-117">Local variables inside a procedure default to public access, and you cannot use any access modifiers on them.</span></span>  
  
- <span data-ttu-id="2b4c0-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="2b4c0-118">**Access Modifiers.**</span></span> <span data-ttu-id="2b4c0-119">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="2b4c0-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="2b4c0-120">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2b4c0-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2b4c0-121">V těchto kontextech lze použít modifikátor `Public`:</span><span class="sxs-lookup"><span data-stu-id="2b4c0-121">The `Public` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="2b4c0-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="2b4c0-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="2b4c0-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="2b4c0-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="2b4c0-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="2b4c0-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="2b4c0-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="2b4c0-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="2b4c0-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="2b4c0-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="2b4c0-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="2b4c0-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="2b4c0-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="2b4c0-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="2b4c0-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="2b4c0-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="2b4c0-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="2b4c0-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="2b4c0-131">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="2b4c0-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="2b4c0-132">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="2b4c0-132">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="2b4c0-133">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="2b4c0-133">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="2b4c0-134">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="2b4c0-134">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="2b4c0-135">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="2b4c0-135">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b4c0-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b4c0-136">See also</span></span>

- [<span data-ttu-id="2b4c0-137">Protected</span><span class="sxs-lookup"><span data-stu-id="2b4c0-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="2b4c0-138">Friend</span><span class="sxs-lookup"><span data-stu-id="2b4c0-138">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="2b4c0-139">Private</span><span class="sxs-lookup"><span data-stu-id="2b4c0-139">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="2b4c0-140">Private Protected</span><span class="sxs-lookup"><span data-stu-id="2b4c0-140">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="2b4c0-141">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="2b4c0-141">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="2b4c0-142">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b4c0-142">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="2b4c0-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="2b4c0-143">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="2b4c0-144">Struktury</span><span class="sxs-lookup"><span data-stu-id="2b4c0-144">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="2b4c0-145">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="2b4c0-145">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
