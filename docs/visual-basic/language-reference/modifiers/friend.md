---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: df0e8ad1990fe7a1aa495e1794c942813cffb5bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="friend-visual-basic"></a><span data-ttu-id="b5d82-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5d82-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="b5d82-103">Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v rámci sestavení, které obsahuje jejich deklarace.</span><span class="sxs-lookup"><span data-stu-id="b5d82-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5d82-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5d82-104">Remarks</span></span>  
 <span data-ttu-id="b5d82-105">V řadě případů budete chtít programování elementů, jako jsou třídy a struktury má být používána celý sestavení, ne jenom komponentou, který deklaruje je.</span><span class="sxs-lookup"><span data-stu-id="b5d82-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="b5d82-106">Však možné, že chcete, aby být přístupné kód mimo sestavení (například pokud aplikace je Proprietární).</span><span class="sxs-lookup"><span data-stu-id="b5d82-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="b5d82-107">Pokud chcete omezit přístup k elementu tímto způsobem, je možné deklarovat pomocí `Friend` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="b5d82-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="b5d82-108">Kód v jiných tříd, struktur a moduly, které jsou zkompilovány do stejného sestavení přístup k veškerým `Friend` elementů v této sestavě.</span><span class="sxs-lookup"><span data-stu-id="b5d82-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="b5d82-109">`Friend`přístup je často úroveň elementům programování aplikace v upřednostňované a `Friend` je přístup k výchozí úroveň rozhraní, modul, třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="b5d82-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="b5d82-110">Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b5d82-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="b5d82-111">Proto deklarace kontext `Friend` element musí být zdrojový soubor, obor názvů, rozhraní, modul, třídu nebo strukturu; nemůže být procedury.</span><span class="sxs-lookup"><span data-stu-id="b5d82-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  
  
 <span data-ttu-id="b5d82-112">Můžete použít `Friend` modifikátor ve spojení s [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) modifikátor ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="b5d82-112">You can use the `Friend` modifier in conjunction with the [Protected](../../../visual-basic/language-reference/modifiers/protected.md) modifier in the same declaration.</span></span> <span data-ttu-id="b5d82-113">Tato kombinace uděluje obě `Friend` přístup a chráněného přístupu na deklarované elementy, které jsou přístupné z libovolné místo ve stejném sestavení, ze své vlastní třídy a z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="b5d82-113">This combination confers both `Friend` access and protected access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="b5d82-114">Můžete zadat `Protected Friend` pouze u členů tříd.</span><span class="sxs-lookup"><span data-stu-id="b5d82-114">You can specify `Protected Friend` only on members of classes.</span></span>  
  
 <span data-ttu-id="b5d82-115">Porovnání `Friend` a dalších přístup modifikátory, najdete v části [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b5d82-115">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5d82-116">Můžete určit, že je sestavení přátelského sestavení, která umožňuje přístup všechny typy a členy, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="b5d82-116">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="b5d82-117">Další informace najdete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b5d82-117">For more information, see [Friend Assemblies](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5d82-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5d82-118">Example</span></span>  
 <span data-ttu-id="b5d82-119">Následující třídy používá `Friend` modifikátor umožňující ostatní programovací elementy v rámci stejného sestavení pro přístup k určitým členům.</span><span class="sxs-lookup"><span data-stu-id="b5d82-119">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a><span data-ttu-id="b5d82-120">Použití</span><span class="sxs-lookup"><span data-stu-id="b5d82-120">Usage</span></span>  
 <span data-ttu-id="b5d82-121">Můžete použít `Friend` modifikátor v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="b5d82-121">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="b5d82-122">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="b5d82-122">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="b5d82-123">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="b5d82-123">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="b5d82-124">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="b5d82-124">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="b5d82-125">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="b5d82-125">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="b5d82-126">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="b5d82-126">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="b5d82-127">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="b5d82-127">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="b5d82-128">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="b5d82-128">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="b5d82-129">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="b5d82-129">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="b5d82-130">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="b5d82-130">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="b5d82-131">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="b5d82-131">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="b5d82-132">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="b5d82-132">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="b5d82-133">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="b5d82-133">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="b5d82-134">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="b5d82-134">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="b5d82-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5d82-135">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="b5d82-136">Public</span><span class="sxs-lookup"><span data-stu-id="b5d82-136">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="b5d82-137">Protected</span><span class="sxs-lookup"><span data-stu-id="b5d82-137">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="b5d82-138">Private</span><span class="sxs-lookup"><span data-stu-id="b5d82-138">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="b5d82-139">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5d82-139">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="b5d82-140">Procedury</span><span class="sxs-lookup"><span data-stu-id="b5d82-140">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="b5d82-141">Struktury</span><span class="sxs-lookup"><span data-stu-id="b5d82-141">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="b5d82-142">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="b5d82-142">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
