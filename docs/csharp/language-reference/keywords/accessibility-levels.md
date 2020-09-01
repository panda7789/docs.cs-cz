---
description: Úrovně dostupnosti – reference jazyka C#
title: Úrovně dostupnosti – reference jazyka C#
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26b8f78595b1406deb371113cf491b80ad7c1474
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127019"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="aaa98-103">Úrovně přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aaa98-103">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="aaa98-104">`public` `protected` `internal` `private` K určení jedné z následujících deklarovaných úrovní dostupnosti pro členy použijte modifikátory přístupu,,, nebo.</span><span class="sxs-lookup"><span data-stu-id="aaa98-104">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="aaa98-105">Deklarovaná přístupnost</span><span class="sxs-lookup"><span data-stu-id="aaa98-105">Declared accessibility</span></span>|<span data-ttu-id="aaa98-106">Význam</span><span class="sxs-lookup"><span data-stu-id="aaa98-106">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="aaa98-107">Přístup není omezen.</span><span class="sxs-lookup"><span data-stu-id="aaa98-107">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="aaa98-108">Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy.</span><span class="sxs-lookup"><span data-stu-id="aaa98-108">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="aaa98-109">Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="aaa98-109">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="aaa98-110">Přístup je omezen na aktuální sestavení nebo typy odvozené z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="aaa98-110">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="aaa98-111">Přístup je omezen na nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="aaa98-111">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="aaa98-112">Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="aaa98-112">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="aaa98-113">Dostupné od verze C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="aaa98-113">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="aaa98-114">Pro člena nebo typ je povolen pouze jeden modifikátor přístupu, s výjimkou použití `protected internal` `private protected` kombinací nebo.</span><span class="sxs-lookup"><span data-stu-id="aaa98-114">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="aaa98-115">Modifikátory přístupu nejsou povolené pro obory názvů.</span><span class="sxs-lookup"><span data-stu-id="aaa98-115">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="aaa98-116">Obory názvů nemají žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="aaa98-116">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="aaa98-117">V závislosti na kontextu, ve kterém je vyvolána deklarace členů, jsou povoleny pouze určité deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="aaa98-117">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="aaa98-118">Pokud v deklaraci členu není zadaný žádný modifikátor přístupu, použije se výchozí přístupnost.</span><span class="sxs-lookup"><span data-stu-id="aaa98-118">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="aaa98-119">Typy nejvyšší úrovně, které nejsou vnořené v jiných typech, mohou mít pouze `internal` nebo `public` přístupnost.</span><span class="sxs-lookup"><span data-stu-id="aaa98-119">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="aaa98-120">Výchozí přístupnost pro tyto typy je `internal` .</span><span class="sxs-lookup"><span data-stu-id="aaa98-120">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="aaa98-121">Vnořené typy, které jsou členy jiných typů, mohou mít deklarované přístupnosti, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="aaa98-121">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="aaa98-122">Členové</span><span class="sxs-lookup"><span data-stu-id="aaa98-122">Members of</span></span>|<span data-ttu-id="aaa98-123">Přístupnost výchozího člena</span><span class="sxs-lookup"><span data-stu-id="aaa98-123">Default member accessibility</span></span>|<span data-ttu-id="aaa98-124">Povolená deklarovaná přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="aaa98-124">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="aaa98-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="aaa98-125">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="aaa98-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="aaa98-126">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="aaa98-127">Přístupnost vnořeného typu závisí na své [doméně přístupnosti](./accessibility-domain.md), která je určena deklarovanou přístupností člena a doménou přístupnosti bezprostředně obsahujícího typu.</span><span class="sxs-lookup"><span data-stu-id="aaa98-127">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="aaa98-128">Nicméně doména přístupnosti vnořeného typu nemůže přesáhnout typ nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="aaa98-128">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="aaa98-129">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aaa98-129">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aaa98-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="aaa98-130">See also</span></span>

- [<span data-ttu-id="aaa98-131">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aaa98-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="aaa98-132">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="aaa98-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="aaa98-133">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aaa98-133">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="aaa98-134">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="aaa98-134">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="aaa98-135">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="aaa98-135">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="aaa98-136">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="aaa98-136">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="aaa98-137">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="aaa98-137">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="aaa98-138">public</span><span class="sxs-lookup"><span data-stu-id="aaa98-138">public</span></span>](./public.md)
- [<span data-ttu-id="aaa98-139">private</span><span class="sxs-lookup"><span data-stu-id="aaa98-139">private</span></span>](./private.md)
- [<span data-ttu-id="aaa98-140">protected</span><span class="sxs-lookup"><span data-stu-id="aaa98-140">protected</span></span>](./protected.md)
- [<span data-ttu-id="aaa98-141">internal</span><span class="sxs-lookup"><span data-stu-id="aaa98-141">internal</span></span>](./internal.md)
