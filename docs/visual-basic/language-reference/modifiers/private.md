---
title: Privátní
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351334"
---
# <a name="private-visual-basic"></a><span data-ttu-id="cd7a0-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd7a0-102">Private (Visual Basic)</span></span>
<span data-ttu-id="cd7a0-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci svého kontextu deklarace, včetně v rámci libovolných obsažených typů.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd7a0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd7a0-104">Remarks</span></span>  
 <span data-ttu-id="cd7a0-105">Pokud programovací element představuje proprietární funkce nebo obsahuje důvěrné údaje, obvykle chcete omezit přístup k němu, co je to možné.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="cd7a0-106">Dosáhnete maximálního omezení tím, že povolíte pouze modul, třídu nebo strukturu, které ji definují k přístupu.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="cd7a0-107">Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Private`.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  

> [!NOTE]
> <span data-ttu-id="cd7a0-108">Můžete také použít modifikátor [privátního chráněného](private-protected.md) přístupu, který zpřístupňuje člena v rámci této třídy a z odvozených tříd umístěných v jeho obsahujícím sestavení.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-108">You can also use the [Private Protected](private-protected.md) access modifier, which makes a member accessible from within that class and from derived classes located in its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="cd7a0-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="cd7a0-109">Rules</span></span>  

- <span data-ttu-id="cd7a0-110">**Kontext deklarace**</span><span class="sxs-lookup"><span data-stu-id="cd7a0-110">**Declaration Context.**</span></span> <span data-ttu-id="cd7a0-111">`Private` můžete použít jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-111">You can use `Private` only at module level.</span></span> <span data-ttu-id="cd7a0-112">To znamená, že kontext deklarace pro prvek `Private` musí být modul, třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-112">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cd7a0-113">Chování</span><span class="sxs-lookup"><span data-stu-id="cd7a0-113">Behavior</span></span>  
  
- <span data-ttu-id="cd7a0-114">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="cd7a0-114">**Access Level.**</span></span> <span data-ttu-id="cd7a0-115">Veškerý kód v kontextu deklarace má přístup k jeho prvkům `Private`.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-115">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="cd7a0-116">To zahrnuje kód v rámci obsaženého typu, jako je vnořená třída nebo výraz přiřazení ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-116">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="cd7a0-117">Žádný kód mimo kontext deklarace má přístup k jeho prvkům `Private`.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-117">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
- <span data-ttu-id="cd7a0-118">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="cd7a0-118">**Access Modifiers.**</span></span> <span data-ttu-id="cd7a0-119">Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*.</span><span class="sxs-lookup"><span data-stu-id="cd7a0-119">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="cd7a0-120">Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cd7a0-120">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="cd7a0-121">V těchto kontextech lze použít modifikátor `Private`:</span><span class="sxs-lookup"><span data-stu-id="cd7a0-121">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="cd7a0-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="cd7a0-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="cd7a0-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="cd7a0-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="cd7a0-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="cd7a0-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="cd7a0-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="cd7a0-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="cd7a0-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="cd7a0-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="cd7a0-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="cd7a0-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="cd7a0-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="cd7a0-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="cd7a0-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="cd7a0-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="cd7a0-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="cd7a0-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="cd7a0-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="cd7a0-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="cd7a0-132">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="cd7a0-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="cd7a0-133">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="cd7a0-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cd7a0-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd7a0-134">See also</span></span>

- [<span data-ttu-id="cd7a0-135">Public</span><span class="sxs-lookup"><span data-stu-id="cd7a0-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="cd7a0-136">Protected</span><span class="sxs-lookup"><span data-stu-id="cd7a0-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="cd7a0-137">Friend</span><span class="sxs-lookup"><span data-stu-id="cd7a0-137">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="cd7a0-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="cd7a0-138">Private Protected</span></span>](./private-protected.md)
- <span data-ttu-id="cd7a0-139">[Chráněné](./protected-friend.md)    [úrovně přístupu typu Friend v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span><span class="sxs-lookup"><span data-stu-id="cd7a0-139">[Protected Friend](./protected-friend.md)    [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)</span></span>
- [<span data-ttu-id="cd7a0-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="cd7a0-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="cd7a0-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="cd7a0-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="cd7a0-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="cd7a0-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
