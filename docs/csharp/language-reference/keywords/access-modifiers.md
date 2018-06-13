---
title: Modifikátory přístupu (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 9629b1727fc210025256724db8db82b13b63b7db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217165"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="e734b-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e734b-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="e734b-103">Modifikátory přístupu jsou klíčová slova slouží k zadání deklarované usnadnění člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="e734b-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="e734b-104">Tato část představuje modifikátory čtyři přístupu:</span><span class="sxs-lookup"><span data-stu-id="e734b-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="e734b-105">Následující šest úrovní přístupu je možné zadat pomocí modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="e734b-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="e734b-106">[`public`](public.md): Přístup není s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="e734b-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="e734b-107">[`protected`](protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="e734b-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="e734b-108">[`internal`](internal.md): Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="e734b-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="e734b-109">[`protected internal`](protected-internal.md): Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="e734b-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="e734b-110">[`private`](private.md): Přístup je omezen na nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="e734b-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="e734b-111">[`private protected`](private-protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="e734b-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="e734b-112">Tato část také obsahuje následující:</span><span class="sxs-lookup"><span data-stu-id="e734b-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="e734b-113">[Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md): pomocí modifikátory čtyři přístupu deklarovat šest úrovní usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="e734b-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="e734b-114">[Doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md): Určuje, kde v částech program může být odkazováno členem.</span><span class="sxs-lookup"><span data-stu-id="e734b-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="e734b-115">[Omezení používání úrovní přístupu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Souhrn omezení pro používání deklarovaná úrovně přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="e734b-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e734b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e734b-116">See Also</span></span>  
 [<span data-ttu-id="e734b-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e734b-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e734b-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e734b-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e734b-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e734b-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e734b-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="e734b-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="e734b-121">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="e734b-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="e734b-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="e734b-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
