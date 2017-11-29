---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a><span data-ttu-id="40f2e-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40f2e-102">Protected (Visual Basic)</span></span>
<span data-ttu-id="40f2e-103">Určuje, že jeden nebo více deklarované programovací elementy jsou přístupné pouze v rámci své vlastní třídy nebo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="40f2e-103">Specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f2e-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40f2e-104">Remarks</span></span>  
 <span data-ttu-id="40f2e-105">Někdy programovací element deklarovaná ve třídě obsahuje citlivá data nebo kód s omezeným přístupem, a chcete omezit přístup k elementu.</span><span class="sxs-lookup"><span data-stu-id="40f2e-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="40f2e-106">Ale pokud ze třídy a očekáváte, že hierarchie odvozených tříd, může být nezbytné pro tyto odvozené třídy přistupovat k datům nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="40f2e-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="40f2e-107">V takovém případě budete chtít elementu, který chcete být přístupné ze základní třídy a z všechny odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="40f2e-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="40f2e-108">Omezit přístup k elementu tímto způsobem, můžou deklarovat její `Protected`.</span><span class="sxs-lookup"><span data-stu-id="40f2e-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="40f2e-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="40f2e-109">Rules</span></span>  
  
-   <span data-ttu-id="40f2e-110">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="40f2e-110">**Declaration Context.**</span></span> <span data-ttu-id="40f2e-111">Můžete použít `Protected` jenom na úrovni třídy.</span><span class="sxs-lookup"><span data-stu-id="40f2e-111">You can use `Protected` only at class level.</span></span> <span data-ttu-id="40f2e-112">To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.</span><span class="sxs-lookup"><span data-stu-id="40f2e-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>  
  
-   <span data-ttu-id="40f2e-113">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="40f2e-113">**Combined Modifiers.**</span></span> <span data-ttu-id="40f2e-114">Můžete použít `Protected` modifikátor společně s [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifikátor ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="40f2e-114">You can use the `Protected` modifier together with the [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifier in the same declaration.</span></span> <span data-ttu-id="40f2e-115">Tato kombinace umožňuje deklarované elementy přístupná odkudkoli do stejného sestavení ze své vlastní třídy a z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="40f2e-115">This combination makes the declared elements accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="40f2e-116">Můžete zadat `Protected Friend` pouze u členů tříd.</span><span class="sxs-lookup"><span data-stu-id="40f2e-116">You can specify `Protected Friend` only on members of classes.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="40f2e-117">Chování</span><span class="sxs-lookup"><span data-stu-id="40f2e-117">Behavior</span></span>  
  
-   <span data-ttu-id="40f2e-118">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="40f2e-118">**Access Level.**</span></span> <span data-ttu-id="40f2e-119">Všechny kódu v třídě mají přístup k jeho elementy.</span><span class="sxs-lookup"><span data-stu-id="40f2e-119">All code in a class can access its elements.</span></span> <span data-ttu-id="40f2e-120">Kód do třídy, která je odvozena ze základní třídy mají přístup ke všem `Protected` elementy základní třídy.</span><span class="sxs-lookup"><span data-stu-id="40f2e-120">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="40f2e-121">To platí pro všechny generací odvození.</span><span class="sxs-lookup"><span data-stu-id="40f2e-121">This is true for all generations of derivation.</span></span> <span data-ttu-id="40f2e-122">To znamená, že třídu přístup `Protected` elementy základní třídy základní třídy a tak dále.</span><span class="sxs-lookup"><span data-stu-id="40f2e-122">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>  
  
     <span data-ttu-id="40f2e-123">Chráněného přístupu není nadmnožinou nebo podmnožinu friend přístup.</span><span class="sxs-lookup"><span data-stu-id="40f2e-123">Protected access is not a superset or subset of friend access.</span></span>  
  
-   <span data-ttu-id="40f2e-124">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="40f2e-124">**Access Modifiers.**</span></span> <span data-ttu-id="40f2e-125">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="40f2e-125">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="40f2e-126">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="40f2e-126">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="40f2e-127">`Protected` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="40f2e-127">The `Protected` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="40f2e-128">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-128">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="40f2e-129">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-129">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="40f2e-130">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-130">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="40f2e-131">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-131">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="40f2e-132">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-132">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="40f2e-133">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-133">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="40f2e-134">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-134">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="40f2e-135">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-135">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="40f2e-136">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-136">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="40f2e-137">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-137">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="40f2e-138">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-138">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="40f2e-139">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="40f2e-139">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="40f2e-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="40f2e-140">See Also</span></span>  
 [<span data-ttu-id="40f2e-141">Veřejné</span><span class="sxs-lookup"><span data-stu-id="40f2e-141">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="40f2e-142">Friend</span><span class="sxs-lookup"><span data-stu-id="40f2e-142">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="40f2e-143">Privátní</span><span class="sxs-lookup"><span data-stu-id="40f2e-143">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
 [<span data-ttu-id="40f2e-144">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40f2e-144">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="40f2e-145">Postupy</span><span class="sxs-lookup"><span data-stu-id="40f2e-145">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="40f2e-146">Struktury</span><span class="sxs-lookup"><span data-stu-id="40f2e-146">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="40f2e-147">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="40f2e-147">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
