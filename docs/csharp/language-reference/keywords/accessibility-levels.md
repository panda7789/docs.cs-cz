---
title: Úrovně usnadnění přístupu – odkaz jazyka C#
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713820"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="3f5b1-102">Úrovně přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3f5b1-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="3f5b1-103">Pomocí modifikátorů `public` `protected`přístupu , , `internal`, nebo `private`, určete jednu z následujících deklarovaných úrovní přístupnosti pro členy.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="3f5b1-104">Deklarovaná přístupnost</span><span class="sxs-lookup"><span data-stu-id="3f5b1-104">Declared accessibility</span></span>|<span data-ttu-id="3f5b1-105">Význam</span><span class="sxs-lookup"><span data-stu-id="3f5b1-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="3f5b1-106">Přístup není omezen.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="3f5b1-107">Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="3f5b1-108">Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="3f5b1-109">Přístup je omezen na aktuální sestavení nebo typy odvozené z obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="3f5b1-110">Přístup je omezen na obsahující typ.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="3f5b1-111">Přístup je omezen na obsahující třídy nebo typy odvozené z obsahující třídy v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="3f5b1-112">K dispozici od C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="3f5b1-113">Pro člena nebo typ je povolen pouze jeden modifikátor přístupu, `protected internal` s výjimkou použití kombinace nebo. `private protected`</span><span class="sxs-lookup"><span data-stu-id="3f5b1-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="3f5b1-114">Modifikátory přístupu nejsou v oborech názvů povoleny.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="3f5b1-115">Obory názvů nemají žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="3f5b1-116">V závislosti na kontextu, ve kterém dojde k deklaraci člena, jsou povoleny pouze určité deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="3f5b1-117">Pokud v deklaraci člena není zadán žádný modifikátor přístupu, použije se výchozí usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="3f5b1-118">Typy nejvyšší úrovně, které nejsou vnořené v `internal` `public` jiných typech, mohou mít pouze nebo usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="3f5b1-119">Výchozí usnadnění přístupu `internal`pro tyto typy je .</span><span class="sxs-lookup"><span data-stu-id="3f5b1-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="3f5b1-120">Vnořené typy, které jsou členy jiných typů, mohou deklarovat přístupnosti, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="3f5b1-121">Členové</span><span class="sxs-lookup"><span data-stu-id="3f5b1-121">Members of</span></span>|<span data-ttu-id="3f5b1-122">Výchozí usnadnění přístupu členů</span><span class="sxs-lookup"><span data-stu-id="3f5b1-122">Default member accessibility</span></span>|<span data-ttu-id="3f5b1-123">Povolená deklarovaná přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="3f5b1-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="3f5b1-124">Žádný</span><span class="sxs-lookup"><span data-stu-id="3f5b1-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="3f5b1-125">Žádný</span><span class="sxs-lookup"><span data-stu-id="3f5b1-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="3f5b1-126">Usnadnění vnořeného typu závisí na [jeho doméně usnadnění přístupu](./accessibility-domain.md), která je určena deklarovanou přístupností člena i doménou usnadnění typu bezprostředně obsahujícího.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="3f5b1-127">Doména usnadnění vnořeného typu však nesmí překročit doménu obsahujícího typu.</span><span class="sxs-lookup"><span data-stu-id="3f5b1-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3f5b1-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f5b1-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3f5b1-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f5b1-129">See also</span></span>

- [<span data-ttu-id="3f5b1-130">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f5b1-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3f5b1-131">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3f5b1-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3f5b1-132">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="3f5b1-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="3f5b1-133">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3f5b1-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="3f5b1-134">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="3f5b1-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="3f5b1-135">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="3f5b1-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="3f5b1-136">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3f5b1-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3f5b1-137">Veřejné</span><span class="sxs-lookup"><span data-stu-id="3f5b1-137">public</span></span>](./public.md)
- [<span data-ttu-id="3f5b1-138">Soukromé</span><span class="sxs-lookup"><span data-stu-id="3f5b1-138">private</span></span>](./private.md)
- [<span data-ttu-id="3f5b1-139">protected</span><span class="sxs-lookup"><span data-stu-id="3f5b1-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="3f5b1-140">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="3f5b1-140">internal</span></span>](./internal.md)
