---
title: "Modifikátory přístupu (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="4697c-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4697c-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="4697c-103">Modifikátory přístupu jsou klíčová slova slouží k zadání deklarované usnadnění člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="4697c-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="4697c-104">Tato část představuje modifikátory čtyři přístupu:</span><span class="sxs-lookup"><span data-stu-id="4697c-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="4697c-105">veřejné</span><span class="sxs-lookup"><span data-stu-id="4697c-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="4697c-106">chráněný</span><span class="sxs-lookup"><span data-stu-id="4697c-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="4697c-107">interní</span><span class="sxs-lookup"><span data-stu-id="4697c-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="4697c-108">privátní</span><span class="sxs-lookup"><span data-stu-id="4697c-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="4697c-109">Následující šest úrovní přístupu je možné zadat pomocí modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="4697c-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="4697c-110">`public`: Přístup není s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="4697c-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="4697c-111">`protected`: Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="4697c-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="4697c-112">`internal`: Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="4697c-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="4697c-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="4697c-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="4697c-114">`private`: Přístup je omezen na nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="4697c-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="4697c-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="4697c-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="4697c-116">Tato část také obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="4697c-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="4697c-117">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md): pomocí modifikátory čtyři přístupu deklarovat šest úrovní usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="4697c-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="4697c-118">[Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md): Určuje, kde v částech program může být odkazováno členem.</span><span class="sxs-lookup"><span data-stu-id="4697c-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="4697c-119">[Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Souhrn omezení pro používání deklarovaná úrovně přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="4697c-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4697c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4697c-120">See Also</span></span>  
 [<span data-ttu-id="4697c-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4697c-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4697c-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4697c-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4697c-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4697c-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="4697c-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="4697c-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="4697c-125">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="4697c-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="4697c-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="4697c-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
