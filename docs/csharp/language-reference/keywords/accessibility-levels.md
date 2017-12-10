---
title: "Úrovně přístupnosti (Referenční dokumentace jazyka C#)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 816ee0fab3fae21bff2ffbfcbfe39d04dcf95025
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="13c94-102">Úrovně přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="13c94-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="13c94-103">Použijte modifikátory přístupu [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md), chcete zadat jednu z následujících deklarovaný úrovně přístupnosti pro členy.</span><span class="sxs-lookup"><span data-stu-id="13c94-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="13c94-104">Deklarované usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="13c94-104">Declared accessibility</span></span>|<span data-ttu-id="13c94-105">Význam</span><span class="sxs-lookup"><span data-stu-id="13c94-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="13c94-106">Přístup není s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="13c94-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="13c94-107">Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="13c94-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="13c94-108">Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="13c94-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="13c94-109">Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="13c94-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="13c94-110">Přístup je omezen na nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="13c94-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="13c94-111">Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="13c94-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="13c94-112">Dostupné od verze jazyka C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="13c94-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="13c94-113">Modifikátor přístupu jenom jeden je povolena pro člena nebo typu, s výjimkou při použití `protected internal` nebo `private protected` kombinace.</span><span class="sxs-lookup"><span data-stu-id="13c94-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="13c94-114">Modifikátory přístupu nejsou povoleny na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="13c94-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="13c94-115">Obory názvů mít žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="13c94-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="13c94-116">V závislosti na kontextu, ve kterém dojde k deklarace členů jsou povolené jenom určité deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="13c94-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="13c94-117">Pokud žádné – modifikátor přístupu je zadaný v deklaraci člen, použije se výchozí usnadnění.</span><span class="sxs-lookup"><span data-stu-id="13c94-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="13c94-118">Typy nejvyšší úrovně, které nejsou vnořené v jiných typech, může mít pouze `internal` nebo `public` usnadnění.</span><span class="sxs-lookup"><span data-stu-id="13c94-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="13c94-119">Je výchozí usnadnění pro tyto typy `internal`.</span><span class="sxs-lookup"><span data-stu-id="13c94-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="13c94-120">Vnořené typy, které jsou členy jiné typy, můžete mít deklarovat přístupnosti, které je uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="13c94-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="13c94-121">Členové</span><span class="sxs-lookup"><span data-stu-id="13c94-121">Members of</span></span>|<span data-ttu-id="13c94-122">Výchozí člen pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="13c94-122">Default member accessibility</span></span>|<span data-ttu-id="13c94-123">Povolené deklarované usnadnění člena</span><span class="sxs-lookup"><span data-stu-id="13c94-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="13c94-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="13c94-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="13c94-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="13c94-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="13c94-126">Usnadnění vnořeného typu závisí na jeho [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md), což je dáno tím deklarované usnadnění člena a doména přístupnosti okamžitě nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="13c94-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="13c94-127">Doména přístupnosti vnořeného typu však nesmí překročit u nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="13c94-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="13c94-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13c94-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13c94-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="13c94-129">See Also</span></span>  
 [<span data-ttu-id="13c94-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13c94-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="13c94-131">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="13c94-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="13c94-132">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13c94-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="13c94-133">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="13c94-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="13c94-134">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="13c94-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="13c94-135">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="13c94-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="13c94-136">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="13c94-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="13c94-137">veřejné</span><span class="sxs-lookup"><span data-stu-id="13c94-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="13c94-138">privátní</span><span class="sxs-lookup"><span data-stu-id="13c94-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="13c94-139">chráněný</span><span class="sxs-lookup"><span data-stu-id="13c94-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="13c94-140">interní</span><span class="sxs-lookup"><span data-stu-id="13c94-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
