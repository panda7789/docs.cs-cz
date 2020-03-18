---
title: Modifikátory přístupu – odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 754949e42771de30cc2dce7e4e610f70ada6dfd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713846"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="1563f-102">Modifikátory přístupu (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1563f-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="1563f-103">Modifikátory přístupu jsou klíčová slova používaná k určení deklarované přístupnosti člena nebo typu.</span><span class="sxs-lookup"><span data-stu-id="1563f-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="1563f-104">Tato část představuje čtyři modifikátory přístupu:</span><span class="sxs-lookup"><span data-stu-id="1563f-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="1563f-105">Pomocí modifikátorů přístupu lze zadat následujících šest úrovní usnadnění:</span><span class="sxs-lookup"><span data-stu-id="1563f-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="1563f-106">[`public`](public.md): Přístup není omezen.</span><span class="sxs-lookup"><span data-stu-id="1563f-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="1563f-107">[`protected`](protected.md): Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="1563f-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="1563f-108">[`internal`](internal.md): Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="1563f-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="1563f-109">[`protected internal`](protected-internal.md): Přístup je omezen na aktuální sestavení nebo typy odvozené z obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="1563f-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="1563f-110">[`private`](private.md): Přístup je omezen na obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="1563f-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="1563f-111">[`private protected`](private-protected.md): Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="1563f-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="1563f-112">V této části jsou také uvedeny následující:</span><span class="sxs-lookup"><span data-stu-id="1563f-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="1563f-113">[Úrovně usnadnění přístupu](./accessibility-levels.md): Použití čtyř modifikátorů přístupu k deklarování šesti úrovní usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="1563f-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="1563f-114">[Doména usnadnění](./accessibility-domain.md): Určuje, na které lze v částech programu odkazovat člena.</span><span class="sxs-lookup"><span data-stu-id="1563f-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="1563f-115">[Omezení používání úrovní přístupnosti](./restrictions-on-using-accessibility-levels.md): Souhrn omezení používání deklarovaných úrovní usnadnění.</span><span class="sxs-lookup"><span data-stu-id="1563f-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1563f-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1563f-116">See also</span></span>

- [<span data-ttu-id="1563f-117">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1563f-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1563f-118">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1563f-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1563f-119">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1563f-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1563f-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="1563f-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="1563f-121">Klíčová slova přístupu</span><span class="sxs-lookup"><span data-stu-id="1563f-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="1563f-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="1563f-122">Modifiers</span></span>](index.md)
