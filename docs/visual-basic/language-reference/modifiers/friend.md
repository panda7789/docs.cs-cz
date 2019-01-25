---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 9be3200300de308a70559536905d1e118a4a5fe4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616196"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="705df-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="705df-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="705df-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný pouze z v rámci sestavení, které obsahuje jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="705df-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="705df-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="705df-104">Remarks</span></span>  
 <span data-ttu-id="705df-105">V mnoha případech chcete programovací prvky, jako například třídy a struktury celé sestavení používané výhradně komponenty, který je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="705df-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="705df-106">Však nemusí je chcete být přístupné kódem mimo sestavení (například pokud je vlastní aplikace).</span><span class="sxs-lookup"><span data-stu-id="705df-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="705df-107">Pokud chcete omezit přístup k prvku tímto způsobem, je možné deklarovat s použitím `Friend` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="705df-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="705df-108">Kód v jiné třídy, struktury a moduly, které jsou kompilovány do stejného sestavení můžete přistupovat ke všem `Friend` prvky v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="705df-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="705df-109">`Friend` přístup je často upřednostňovanou úroveň pro programovací prvky aplikace, a `Friend` je přístup k výchozím úrovně rozhraní, modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="705df-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="705df-110">Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="705df-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="705df-111">Proto deklarace kontext `Friend` element musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídy nebo struktury; nemůže být procedury.</span><span class="sxs-lookup"><span data-stu-id="705df-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="705df-112">Můžete také použít [Protected Friend](protected-friend.md) modifikátor přístupu, který zpřístupňuje člen třídy z v rámci této třídy z odvozené třídy a ze stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="705df-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="705df-113">Chcete-li omezit přístup ke členovi v rámci své třídy a z odvozených tříd ve stejném sestavení, je použít [Private Protected](private-protected.md) modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="705df-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="705df-114">Porovnání `Friend` a dalších modifikátorů přístupu, najdete v článku [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="705df-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="705df-115">Můžete určit, že jiné sestavení je sestavení typu friend, což umožňuje přístup ke všem typy a členy, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="705df-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="705df-116">Další informace najdete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="705df-116">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="705df-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="705df-117">Example</span></span>  
 <span data-ttu-id="705df-118">Následující třídy používá `Friend` modifikátor umožňující dalších programovacích prvků v rámci stejného sestavení pro přístup k určitým členům.</span><span class="sxs-lookup"><span data-stu-id="705df-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="705df-119">Použití</span><span class="sxs-lookup"><span data-stu-id="705df-119">Usage</span></span>  
 <span data-ttu-id="705df-120">Můžete použít `Friend` modifikátor v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="705df-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="705df-121">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="705df-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="705df-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="705df-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="705df-123">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="705df-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="705df-124">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="705df-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="705df-125">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="705df-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="705df-126">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="705df-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="705df-127">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="705df-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="705df-128">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="705df-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="705df-129">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="705df-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="705df-130">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="705df-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="705df-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="705df-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="705df-132">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="705df-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="705df-133">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="705df-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="705df-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="705df-134">See also</span></span>
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="705df-135">Public</span><span class="sxs-lookup"><span data-stu-id="705df-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="705df-136">Protected</span><span class="sxs-lookup"><span data-stu-id="705df-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="705df-137">Private</span><span class="sxs-lookup"><span data-stu-id="705df-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="705df-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="705df-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="705df-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="705df-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="705df-140">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="705df-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="705df-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="705df-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="705df-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="705df-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="705df-143">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="705df-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
