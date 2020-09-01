---
description: Modifikátory přístupu – reference jazyka C#
title: Modifikátory přístupu – reference jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 2ea7a65c23b6a1edee572f6f6ff6c52d14358408
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127149"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="25658-103">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="25658-103">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="25658-104">Modifikátory přístupu jsou klíčová slova sloužící k určení deklarovaného přístupnosti člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="25658-104">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="25658-105">V této části se seznámíte se čtyřmi modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="25658-105">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="25658-106">Pomocí modifikátorů přístupu lze zadat následující šest úrovní dostupnosti:</span><span class="sxs-lookup"><span data-stu-id="25658-106">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="25658-107">[`public`](public.md): Přístup není omezený.</span><span class="sxs-lookup"><span data-stu-id="25658-107">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="25658-108">[`protected`](protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="25658-108">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="25658-109">[`internal`](internal.md): Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="25658-109">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="25658-110">[`protected internal`](protected-internal.md): Přístup je omezen na aktuální sestavení nebo typy odvozené z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="25658-110">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="25658-111">[`private`](private.md): Přístup je omezen na nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="25658-111">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="25658-112">[`private protected`](private-protected.md): Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="25658-112">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="25658-113">Tato část také obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="25658-113">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="25658-114">[Úrovně dostupnosti](./accessibility-levels.md): pomocí čtyř modifikátorů přístupu deklarujete šest úrovní dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="25658-114">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="25658-115">[Doména přístupnosti](./accessibility-domain.md): Určuje, kde lze v sekcích programu odkazovat na člena.</span><span class="sxs-lookup"><span data-stu-id="25658-115">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="25658-116">[Omezení používání úrovní dostupnosti](./restrictions-on-using-accessibility-levels.md): Shrnutí omezení používání deklarované úrovně přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="25658-116">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25658-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="25658-117">See also</span></span>

- [<span data-ttu-id="25658-118">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25658-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25658-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="25658-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="25658-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="25658-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="25658-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="25658-121">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="25658-122">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="25658-122">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="25658-123">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="25658-123">Modifiers</span></span>](index.md)
