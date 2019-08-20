---
title: Úrovně dostupnosti – C# referenční informace
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602384"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="60067-102">Úrovně přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="60067-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="60067-103">K určení jedné z následujících deklarovaných `protected`úrovní dostupnosti pro `private`členy použijte modifikátory `public` `internal`přístupu,,, nebo.</span><span class="sxs-lookup"><span data-stu-id="60067-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="60067-104">Deklarovaná přístupnost</span><span class="sxs-lookup"><span data-stu-id="60067-104">Declared accessibility</span></span>|<span data-ttu-id="60067-105">Význam</span><span class="sxs-lookup"><span data-stu-id="60067-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="60067-106">Přístup není omezen.</span><span class="sxs-lookup"><span data-stu-id="60067-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="60067-107">Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy.</span><span class="sxs-lookup"><span data-stu-id="60067-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="60067-108">Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="60067-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="60067-109">Přístup je omezen na aktuální sestavení nebo typy odvozené z nadřazené třídy.</span><span class="sxs-lookup"><span data-stu-id="60067-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="60067-110">Přístup je omezen na nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="60067-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="60067-111">Přístup je omezen na obsahující třídu nebo typy odvozené z obsažené třídy v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="60067-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="60067-112">K dispozici od C# verze 7,2.</span><span class="sxs-lookup"><span data-stu-id="60067-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="60067-113">Pro člena nebo typ je povolen pouze jeden modifikátor přístupu, s výjimkou použití `protected internal` kombinací nebo. `private protected`</span><span class="sxs-lookup"><span data-stu-id="60067-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="60067-114">Modifikátory přístupu nejsou povolené pro obory názvů.</span><span class="sxs-lookup"><span data-stu-id="60067-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="60067-115">Obory názvů nemají žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="60067-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="60067-116">V závislosti na kontextu, ve kterém je vyvolána deklarace členů, jsou povoleny pouze určité deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="60067-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="60067-117">Pokud v deklaraci členu není zadaný žádný modifikátor přístupu, použije se výchozí přístupnost.</span><span class="sxs-lookup"><span data-stu-id="60067-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="60067-118">Typy nejvyšší úrovně, které nejsou vnořené v jiných typech, mohou mít `internal` pouze nebo `public` přístupnost.</span><span class="sxs-lookup"><span data-stu-id="60067-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="60067-119">Výchozí přístupnost pro tyto typy je `internal`.</span><span class="sxs-lookup"><span data-stu-id="60067-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="60067-120">Vnořené typy, které jsou členy jiných typů, mohou mít deklarované přístupnosti, jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="60067-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="60067-121">Členové</span><span class="sxs-lookup"><span data-stu-id="60067-121">Members of</span></span>|<span data-ttu-id="60067-122">Přístupnost výchozího člena</span><span class="sxs-lookup"><span data-stu-id="60067-122">Default member accessibility</span></span>|<span data-ttu-id="60067-123">Povolená deklarovaná přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="60067-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="60067-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="60067-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="60067-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="60067-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="60067-126">Přístupnost vnořeného typu závisí na své [doméně](./accessibility-domain.md)přístupnosti, která je určena deklarovanou přístupností člena a doménou přístupnosti bezprostředně obsahujícího typu.</span><span class="sxs-lookup"><span data-stu-id="60067-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="60067-127">Nicméně doména přístupnosti vnořeného typu nemůže přesáhnout typ nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="60067-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="60067-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60067-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="60067-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="60067-129">See also</span></span>

- [<span data-ttu-id="60067-130">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="60067-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="60067-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="60067-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="60067-132">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="60067-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="60067-133">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="60067-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="60067-134">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="60067-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="60067-135">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="60067-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="60067-136">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="60067-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="60067-137">public</span><span class="sxs-lookup"><span data-stu-id="60067-137">public</span></span>](./public.md)
- [<span data-ttu-id="60067-138">private</span><span class="sxs-lookup"><span data-stu-id="60067-138">private</span></span>](./private.md)
- [<span data-ttu-id="60067-139">protected</span><span class="sxs-lookup"><span data-stu-id="60067-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="60067-140">internal</span><span class="sxs-lookup"><span data-stu-id="60067-140">internal</span></span>](./internal.md)
