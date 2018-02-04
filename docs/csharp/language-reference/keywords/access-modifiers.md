---
title: "Modifikátory přístupu (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d63cf724a2364059e5f3327254a9ec95f7493e5e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="dbce4-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dbce4-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="dbce4-103">Modifikátory přístupu jsou klíčová slova slouží k zadání deklarované usnadnění člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="dbce4-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="dbce4-104">Tato část představuje modifikátory čtyři přístupu:</span><span class="sxs-lookup"><span data-stu-id="dbce4-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="dbce4-105">Následující šest úrovní přístupu je možné zadat pomocí modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="dbce4-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="dbce4-106">[`public`](public.md): Přístup není s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="dbce4-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="dbce4-107">[`protected`](protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="dbce4-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="dbce4-108">[`internal`](internal.md): Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="dbce4-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="dbce4-109">[`protected internal`](protected-internal.md): Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="dbce4-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="dbce4-110">[`private`](private.md): Přístup je omezen na nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="dbce4-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="dbce4-111">[`private protected`](private-protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="dbce4-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="dbce4-112">Tato část také obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="dbce4-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="dbce4-113">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md): pomocí modifikátory čtyři přístupu deklarovat šest úrovní usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="dbce4-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="dbce4-114">[Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md): Určuje, kde v částech program může být odkazováno členem.</span><span class="sxs-lookup"><span data-stu-id="dbce4-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="dbce4-115">[Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Souhrn omezení pro používání deklarovaná úrovně přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="dbce4-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbce4-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="dbce4-116">See Also</span></span>  
 [<span data-ttu-id="dbce4-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dbce4-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dbce4-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dbce4-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dbce4-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dbce4-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="dbce4-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="dbce4-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="dbce4-121">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="dbce4-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="dbce4-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="dbce4-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
