---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a><span data-ttu-id="bf8d3-102">Private (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf8d3-102">Private (Visual Basic)</span></span>
<span data-ttu-id="bf8d3-103">Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v kontextu jejich deklarace, včetně v rámci všechny obsažené typy.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-103">Specifies that one or more declared programming elements are accessible only from within their declaration context, including from within any contained types.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf8d3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf8d3-104">Remarks</span></span>  
 <span data-ttu-id="bf8d3-105">Pokud programovací element představuje speciálních funkcí, nebo obsahuje důvěrných dat, obvykle chcete omezit přístup k němu jako výhradně.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-105">If a programming element represents proprietary functionality, or contains confidential data, you usually want to limit access to it as strictly as possible.</span></span> <span data-ttu-id="bf8d3-106">Maximální omezení můžete dosáhnout tím, že pouze modulu, třídu nebo strukturu, která definuje, aby k němu přístup.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-106">You achieve the maximum limitation by allowing only the module, class, or structure that defines it to access it.</span></span> <span data-ttu-id="bf8d3-107">Omezit přístup k elementu tímto způsobem, můžou deklarovat její `Private`.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-107">To limit access to an element in this way, you can declare it with `Private`.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="bf8d3-108">Pravidla</span><span class="sxs-lookup"><span data-stu-id="bf8d3-108">Rules</span></span>  
  
-   <span data-ttu-id="bf8d3-109">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="bf8d3-109">**Declaration Context.**</span></span> <span data-ttu-id="bf8d3-110">Můžete použít `Private` jenom na úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-110">You can use `Private` only at module level.</span></span> <span data-ttu-id="bf8d3-111">To znamená kontext deklarace `Private` element musí být modul, třídu nebo strukturu a nemůže být zdrojový soubor, obor názvů, rozhraní nebo postupu.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-111">This means the declaration context for a `Private` element must be a module, class, or structure, and cannot be a source file, namespace, interface, or procedure.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="bf8d3-112">Chování</span><span class="sxs-lookup"><span data-stu-id="bf8d3-112">Behavior</span></span>  
  
-   <span data-ttu-id="bf8d3-113">**Úroveň přístupu.**</span><span class="sxs-lookup"><span data-stu-id="bf8d3-113">**Access Level.**</span></span> <span data-ttu-id="bf8d3-114">Všechny kódu v rámci kontextu deklarace můžete přístup k jeho `Private` elementy.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-114">All code within a declaration context can access its `Private` elements.</span></span> <span data-ttu-id="bf8d3-115">To zahrnuje kódu v rámci omezením typu, například vnořené třídy nebo výraz přiřazení ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-115">This includes code within a contained type, such as a nested class or an assignment expression in an enumeration.</span></span> <span data-ttu-id="bf8d3-116">Žádný kód mimo kontext deklarace můžete přístup k jeho `Private` elementy.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-116">No code outside of the declaration context can access its `Private` elements.</span></span>  
  
-   <span data-ttu-id="bf8d3-117">**Modifikátory přístupu.**</span><span class="sxs-lookup"><span data-stu-id="bf8d3-117">**Access Modifiers.**</span></span> <span data-ttu-id="bf8d3-118">Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*.</span><span class="sxs-lookup"><span data-stu-id="bf8d3-118">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="bf8d3-119">Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="bf8d3-119">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="bf8d3-120">`Private` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="bf8d3-120">The `Private` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="bf8d3-121">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="bf8d3-122">Const – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-122">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="bf8d3-123">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-123">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="bf8d3-124">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-124">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="bf8d3-125">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-125">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="bf8d3-126">Enum – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-126">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="bf8d3-127">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-127">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="bf8d3-128">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-128">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="bf8d3-129">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-129">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="bf8d3-130">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-130">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="bf8d3-131">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-131">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="bf8d3-132">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="bf8d3-132">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="bf8d3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf8d3-133">See Also</span></span>  
 [<span data-ttu-id="bf8d3-134">Veřejné</span><span class="sxs-lookup"><span data-stu-id="bf8d3-134">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="bf8d3-135">Chráněný</span><span class="sxs-lookup"><span data-stu-id="bf8d3-135">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="bf8d3-136">Friend</span><span class="sxs-lookup"><span data-stu-id="bf8d3-136">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="bf8d3-137">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bf8d3-137">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="bf8d3-138">Postupy</span><span class="sxs-lookup"><span data-stu-id="bf8d3-138">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [<span data-ttu-id="bf8d3-139">Struktury</span><span class="sxs-lookup"><span data-stu-id="bf8d3-139">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="bf8d3-140">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="bf8d3-140">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
