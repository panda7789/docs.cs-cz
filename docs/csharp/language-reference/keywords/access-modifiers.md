---
title: Modifikátory přístupu – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 754949e42771de30cc2dce7e4e610f70ada6dfd4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713846"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="b3f1d-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b3f1d-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="b3f1d-103">Modifikátory přístupu jsou klíčová slova sloužící k určení deklarovaného přístupnosti člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="b3f1d-104">V této části se seznámíte se čtyřmi modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="b3f1d-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="b3f1d-105">Pomocí modifikátorů přístupu lze zadat následující šest úrovní dostupnosti:</span><span class="sxs-lookup"><span data-stu-id="b3f1d-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="b3f1d-106">[`public`](public.md): přístup není omezený.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="b3f1d-107">[`protected`](protected.md): přístup je omezen na obsahující třídu nebo typy odvozené z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="b3f1d-108">[`internal`](internal.md): přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="b3f1d-109">[`protected internal`](protected-internal.md): přístup je omezen na aktuální sestavení nebo typy odvozené z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="b3f1d-110">[`private`](private.md): přístup je omezen na nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="b3f1d-111">[`private protected`](private-protected.md): přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="b3f1d-112">Tato část také obsahuje následující informace:</span><span class="sxs-lookup"><span data-stu-id="b3f1d-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="b3f1d-113">[Úrovně dostupnosti](./accessibility-levels.md): pomocí čtyř modifikátorů přístupu deklarujete šest úrovní dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="b3f1d-114">[Doména přístupnosti](./accessibility-domain.md): Určuje, kde lze v sekcích programu odkazovat na člena.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="b3f1d-115">[Omezení používání úrovní dostupnosti](./restrictions-on-using-accessibility-levels.md): Shrnutí omezení používání deklarované úrovně přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="b3f1d-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f1d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3f1d-116">See also</span></span>

- [<span data-ttu-id="b3f1d-117">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b3f1d-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b3f1d-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b3f1d-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b3f1d-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3f1d-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b3f1d-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="b3f1d-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="b3f1d-121">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="b3f1d-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="b3f1d-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="b3f1d-122">Modifiers</span></span>](index.md)
