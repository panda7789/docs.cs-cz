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
ms.openlocfilehash: 98f8ed947c9f4376c5778011a3a91ca8b094f9ec
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351563"
---
# <a name="friend-visual-basic"></a><span data-ttu-id="7834c-102">Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7834c-102">Friend (Visual Basic)</span></span>
<span data-ttu-id="7834c-103">Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci sestavení, které obsahuje jejich deklaraci.</span><span class="sxs-lookup"><span data-stu-id="7834c-103">Specifies that one or more declared programming elements are accessible only from within the assembly that contains their declaration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7834c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7834c-104">Remarks</span></span>  
 <span data-ttu-id="7834c-105">V mnoha případech požadujete, aby byly programovací prvky, jako jsou třídy a struktury, použity celým sestavením, nikoli pouze komponentou, která je deklaruje.</span><span class="sxs-lookup"><span data-stu-id="7834c-105">In many cases, you want programming elements such as classes and structures to be used by the entire assembly, not only by the component that declares them.</span></span> <span data-ttu-id="7834c-106">Je však možné, že nechcete, aby byly přístupné pomocí kódu mimo sestavení (například pokud je aplikace proprietární).</span><span class="sxs-lookup"><span data-stu-id="7834c-106">However, you might not want them to be accessible by code outside the assembly (for example, if the application is proprietary).</span></span> <span data-ttu-id="7834c-107">Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí modifikátoru `Friend`.</span><span class="sxs-lookup"><span data-stu-id="7834c-107">If you want to limit access to an element in this way, you can declare it by using the `Friend` modifier.</span></span>  
  
 <span data-ttu-id="7834c-108">Kód v jiných třídách, strukturách a modulech, které jsou zkompilovány do stejného sestavení, mají přístup ke všem prvkům `Friend` v tomto sestavení.</span><span class="sxs-lookup"><span data-stu-id="7834c-108">Code in other classes, structures, and modules that are compiled to the same assembly can access all the `Friend` elements in that assembly.</span></span>  
  
 <span data-ttu-id="7834c-109">přístup k `Friend` je často upřednostňovanou úrovní pro programovací prvky aplikace a `Friend` je výchozí úrovní přístupu rozhraní, modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="7834c-109">`Friend` access is often the preferred level for an application's programming elements, and `Friend` is the default access level of an interface, a module, a class, or a structure.</span></span>  
  
 <span data-ttu-id="7834c-110">`Friend` můžete použít jenom na úrovni modulu, rozhraní nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7834c-110">You can use `Friend` only at the module, interface, or namespace level.</span></span> <span data-ttu-id="7834c-111">Proto kontext deklarace pro prvek `Friend` musí být zdrojový soubor, obor názvů, rozhraní, modul, třída nebo struktura; nemůže se jednat o proceduru.</span><span class="sxs-lookup"><span data-stu-id="7834c-111">Therefore, the declaration context for a `Friend` element must be a source file, a namespace, an interface, a module, a class, or a structure; it can't be a procedure.</span></span>  

> [!NOTE]
> <span data-ttu-id="7834c-112">Můžete použít také modifikátor [Protected Friend](protected-friend.md) Access, který zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná.</span><span class="sxs-lookup"><span data-stu-id="7834c-112">You can also use the [Protected Friend](protected-friend.md) access modifier, which makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span> <span data-ttu-id="7834c-113">Chcete-li omezit přístup ke členovi z jeho třídy a z odvozených tříd ve stejném sestavení, použijte modifikátor [privátního chráněného](private-protected.md) přístupu.</span><span class="sxs-lookup"><span data-stu-id="7834c-113">To restrict access to a member from within its class and from derived classes in the same assembly, you use the [Private Protected](private-protected.md) access modifier.</span></span>

 <span data-ttu-id="7834c-114">Porovnání `Friend` a dalších modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7834c-114">For a comparison of `Friend` and the other access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7834c-115">Můžete určit, že jiné sestavení je sestavení typu Friend, které umožňuje přístup ke všem typům a členům, které jsou označeny jako `Friend`.</span><span class="sxs-lookup"><span data-stu-id="7834c-115">You can specify that another assembly is a friend assembly, which allows it to access all types and members that are marked as `Friend`.</span></span> <span data-ttu-id="7834c-116">Další informace naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).</span><span class="sxs-lookup"><span data-stu-id="7834c-116">For more information, see [Friend Assemblies](../../../standard/assembly/friend.md).</span></span>

## <a name="example"></a><span data-ttu-id="7834c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="7834c-117">Example</span></span>  
 <span data-ttu-id="7834c-118">Následující třída používá modifikátor `Friend`, aby umožnil ostatním programovacím prvkům v rámci stejného sestavení získat přístup k určitým členům.</span><span class="sxs-lookup"><span data-stu-id="7834c-118">The following class uses the `Friend` modifier to allow other programming elements within the same assembly to access certain members.</span></span>  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
## <a name="usage"></a><span data-ttu-id="7834c-119">Využití</span><span class="sxs-lookup"><span data-stu-id="7834c-119">Usage</span></span>  
 <span data-ttu-id="7834c-120">V těchto kontextech můžete použít modifikátor `Friend`:</span><span class="sxs-lookup"><span data-stu-id="7834c-120">You can use the `Friend` modifier in these contexts:</span></span>  
  
 [<span data-ttu-id="7834c-121">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="7834c-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="7834c-122">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="7834c-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="7834c-123">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="7834c-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="7834c-124">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="7834c-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="7834c-125">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="7834c-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="7834c-126">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="7834c-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="7834c-127">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="7834c-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="7834c-128">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="7834c-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="7834c-129">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="7834c-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="7834c-130">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="7834c-130">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [<span data-ttu-id="7834c-131">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="7834c-131">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="7834c-132">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="7834c-132">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="7834c-133">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="7834c-133">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7834c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7834c-134">See also</span></span>

- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [<span data-ttu-id="7834c-135">Public</span><span class="sxs-lookup"><span data-stu-id="7834c-135">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="7834c-136">Protected</span><span class="sxs-lookup"><span data-stu-id="7834c-136">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="7834c-137">Private</span><span class="sxs-lookup"><span data-stu-id="7834c-137">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="7834c-138">Private Protected</span><span class="sxs-lookup"><span data-stu-id="7834c-138">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="7834c-139">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="7834c-139">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="7834c-140">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7834c-140">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="7834c-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="7834c-141">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="7834c-142">Struktury</span><span class="sxs-lookup"><span data-stu-id="7834c-142">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7834c-143">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="7834c-143">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
