---
title: Friend
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
ms.openlocfilehash: 4ac8e5942cf6097642ec111992ebfcdb91e8d7c1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392168"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="e3fb3-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3fb3-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="e3fb3-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci sestavení, které obsahuje jejich deklaraci.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3fb3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3fb3-104">Remarks</span></span>  
 <span data-ttu-id="e3fb3-105">V mnoha případech požadujete, aby byly programovací prvky, jako jsou třídy a struktury, použity celým sestavením, nikoli pouze komponentou, která je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="e3fb3-106">Je však možné, že nechcete, aby byly přístupné pomocí kódu mimo sestavení (například pokud je aplikace proprietární).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="e3fb3-107">Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Friend` modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="e3fb3-108">Kód v jiných třídách, strukturách a modulech, které jsou zkompilovány do stejného sestavení, mají přístup ke všem `Friend` prvkům v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="e3fb3-109">`Friend`přístup je často upřednostňovanou úrovní pro programovací prvky aplikace a `Friend` je výchozí úrovní přístupu rozhraní, modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="e3fb3-110">Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="e3fb3-111">Proto kontext deklarace pro `Friend` prvek musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura. nemůže to být procedura.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="e3fb3-112">Můžete použít také modifikátor [Protected Friend](protected-friend.md) Access, který zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="e3fb3-113">Chcete-li omezit přístup ke členovi z jeho třídy a z odvozených tříd ve stejném sestavení, použijte modifikátor [privátního chráněného](private-protected.md) přístupu.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="e3fb3-114">Porovnání `Friend` a ostatní modifikátory přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3fb3-115">Můžete určit, že jiné sestavení je sestavení typu Friend, které umožňuje přístup ke všem typům a členům, které jsou označeny jako `Friend` .</span><span class="sxs-lookup"><span data-stu-id="e3fb3-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="e3fb3-116">Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="e3fb3-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="e3fb3-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3fb3-117">Example</span></span>  
 <span data-ttu-id="e3fb3-118">Následující třída používá `Friend` Modifikátor k povolení přístupu k určitým členům jiným programovacím prvkům v rámci stejného sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3fb3-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="e3fb3-119">Využití</span><span class="sxs-lookup"><span data-stu-id="e3fb3-119">Usage</span></span>  
 <span data-ttu-id="e3fb3-120">`Friend`V těchto kontextech můžete použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="e3fb3-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="e3fb3-121">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-121">Class Statement</span></span>](../statements/class-statement.md)  
  
 [<span data-ttu-id="e3fb3-122">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-122">Const Statement</span></span>](../statements/const-statement.md)  
  
 [<span data-ttu-id="e3fb3-123">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-123">Declare Statement</span></span>](../statements/declare-statement.md)  
  
 [<span data-ttu-id="e3fb3-124">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-124">Delegate Statement</span></span>](../statements/delegate-statement.md)  
  
 [<span data-ttu-id="e3fb3-125">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-125">Dim Statement</span></span>](../statements/dim-statement.md)  
  
 [<span data-ttu-id="e3fb3-126">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-126">Enum Statement</span></span>](../statements/enum-statement.md)  
  
 [<span data-ttu-id="e3fb3-127">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-127">Event Statement</span></span>](../statements/event-statement.md)  
  
 [<span data-ttu-id="e3fb3-128">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-128">Function Statement</span></span>](../statements/function-statement.md)  
  
 [<span data-ttu-id="e3fb3-129">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-129">Interface Statement</span></span>](../statements/interface-statement.md)  
  
 [<span data-ttu-id="e3fb3-130">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-130">Module Statement</span></span>](../statements/module-statement.md)  
  
 [<span data-ttu-id="e3fb3-131">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-131">Property Statement</span></span>](../statements/property-statement.md)  
  
 [<span data-ttu-id="e3fb3-132">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-132">Structure Statement</span></span>](../statements/structure-statement.md)  
  
 [<span data-ttu-id="e3fb3-133">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="e3fb3-133">Sub Statement</span></span>](../statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="e3fb3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3fb3-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="e3fb3-135">Republik</span><span class="sxs-lookup"><span data-stu-id="e3fb3-135">Public</span></span>](public.md)
- [<span data-ttu-id="e3fb3-136">Proti</span><span class="sxs-lookup"><span data-stu-id="e3fb3-136">Protected</span></span>](protected.md)
- [<span data-ttu-id="e3fb3-137">Hlášen</span><span class="sxs-lookup"><span data-stu-id="e3fb3-137">Private</span></span>](private.md)
- [<span data-ttu-id="e3fb3-138">Soukromé chráněné</span><span class="sxs-lookup"><span data-stu-id="e3fb3-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="e3fb3-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="e3fb3-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="e3fb3-140">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3fb3-140">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="e3fb3-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="e3fb3-141">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="e3fb3-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="e3fb3-142">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="e3fb3-143">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="e3fb3-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
