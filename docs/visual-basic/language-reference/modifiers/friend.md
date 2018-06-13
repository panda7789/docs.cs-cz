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
ms.openlocfilehash: d906fc8ada19f22059da44acbd76dd07dacd4801
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234586"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="1b130-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1b130-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="1b130-103">Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v rámci sestavení, které obsahuje jejich deklarace.</span><span class="sxs-lookup"><span data-stu-id="1b130-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b130-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1b130-104">Remarks</span></span>  
 <span data-ttu-id="1b130-105">V řadě případů budete chtít programování elementů, jako jsou třídy a struktury má být používána celý sestavení, ne jenom komponentou, který deklaruje je.</span><span class="sxs-lookup"><span data-stu-id="1b130-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="1b130-106">Však možné, že chcete, aby být přístupné kód mimo sestavení (například pokud aplikace je Proprietární).</span><span class="sxs-lookup"><span data-stu-id="1b130-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="1b130-107">Pokud chcete omezit přístup k elementu tímto způsobem, je možné deklarovat pomocí `Friend` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="1b130-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="1b130-108">Kód v jiných tříd, struktur a moduly, které jsou zkompilovány do stejného sestavení přístup k veškerým `Friend` elementů v této sestavě.</span><span class="sxs-lookup"><span data-stu-id="1b130-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="1b130-109">`Friend` přístup je často úroveň elementům programování aplikace v upřednostňované a `Friend` je přístup k výchozí úroveň rozhraní, modul, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="1b130-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="1b130-110">Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="1b130-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="1b130-111">Proto deklarace kontext `Friend` element musí být zdrojový soubor, obor názvů, rozhraní, modul, třídu nebo strukturu; nemůže být procedury.</span><span class="sxs-lookup"><span data-stu-id="1b130-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="1b130-112">Můžete také [Protected Friend](protected-friend.md) – modifikátor přístupu, které umožňuje přístup z v rámci třídy, v rámci odvozené třídy a do stejného sestavení, ve kterém je třída definovaná člena třídy.</span><span class="sxs-lookup"><span data-stu-id="1b130-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="1b130-113">Chcete-li omezit přístup k člena z v rámci své třídy a z odvozené třídy ve stejném sestavení, použijte [privátní chráněné](private-protected.md) – modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="1b130-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="1b130-114">Porovnání `Friend` a dalších přístup modifikátory, najdete v části [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="1b130-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1b130-115">Můžete určit, že je sestavení přátelského sestavení, která umožňuje přístup všechny typy a členy, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="1b130-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="1b130-116">Další informace najdete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="1b130-116">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b130-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b130-117">Example</span></span>  
 <span data-ttu-id="1b130-118">Následující třídy používá `Friend` modifikátor umožňující ostatní programovací elementy v rámci stejného sestavení pro přístup k určitým členům.</span><span class="sxs-lookup"><span data-stu-id="1b130-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="1b130-119">Použití</span><span class="sxs-lookup"><span data-stu-id="1b130-119">Usage</span></span>  
 <span data-ttu-id="1b130-120">Můžete použít `Friend` modifikátor v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="1b130-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="1b130-121">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="1b130-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="1b130-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="1b130-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="1b130-123">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="1b130-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="1b130-124">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="1b130-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="1b130-125">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="1b130-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="1b130-126">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="1b130-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="1b130-127">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="1b130-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="1b130-128">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="1b130-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="1b130-129">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="1b130-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="1b130-130">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="1b130-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="1b130-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="1b130-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="1b130-132">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="1b130-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="1b130-133">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="1b130-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="1b130-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b130-134">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="1b130-135">Public</span><span class="sxs-lookup"><span data-stu-id="1b130-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="1b130-136">Protected</span><span class="sxs-lookup"><span data-stu-id="1b130-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="1b130-137">Private</span><span class="sxs-lookup"><span data-stu-id="1b130-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 <span data-ttu-id="1b130-138">[Privátní chráněný](./private-protected.md) </span><span class="sxs-lookup"><span data-stu-id="1b130-138">[Private Protected](./private-protected.md) </span></span>  
 <span data-ttu-id="1b130-139">[Chráněné Friend](./protected-friend.md) </span><span class="sxs-lookup"><span data-stu-id="1b130-139">[Protected Friend](./protected-friend.md) </span></span>  
 [<span data-ttu-id="1b130-140">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1b130-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="1b130-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="1b130-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="1b130-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="1b130-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="1b130-143">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="1b130-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
