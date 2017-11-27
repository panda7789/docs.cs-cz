---
title: "Úrovně přístupnosti (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="58f0c-102">Úrovně přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="58f0c-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="58f0c-103">Použijte modifikátory přístupu [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md), chcete zadat jednu z následujících deklarovaný úrovně přístupnosti pro členy.</span><span class="sxs-lookup"><span data-stu-id="58f0c-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="58f0c-104">Deklarované usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="58f0c-104">Declared accessibility</span></span>|<span data-ttu-id="58f0c-105">Význam</span><span class="sxs-lookup"><span data-stu-id="58f0c-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="58f0c-106">Přístup není s omezeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="58f0c-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="58f0c-107">Přístup je omezen na obsahující třídu nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="58f0c-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="58f0c-108">Přístup je omezen na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="58f0c-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="58f0c-109">Přístup je omezen na aktuální sestavení nebo typy odvozené od obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="58f0c-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="58f0c-110">Přístup je omezen na nadřazeném typu.</span><span class="sxs-lookup"><span data-stu-id="58f0c-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="58f0c-111">Přístup je omezen na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="58f0c-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="58f0c-112">Modifikátor přístupu jenom jeden je povolena pro člena nebo typu, s výjimkou při použití `protected internal` nebo `private protected` kombinace.</span><span class="sxs-lookup"><span data-stu-id="58f0c-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="58f0c-113">Modifikátory přístupu nejsou povoleny na obory názvů.</span><span class="sxs-lookup"><span data-stu-id="58f0c-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="58f0c-114">Obory názvů mít žádná omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="58f0c-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="58f0c-115">V závislosti na kontextu, ve kterém dojde k deklarace členů jsou povolené jenom určité deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="58f0c-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="58f0c-116">Pokud žádné – modifikátor přístupu je zadaný v deklaraci člen, použije se výchozí usnadnění.</span><span class="sxs-lookup"><span data-stu-id="58f0c-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="58f0c-117">Typy nejvyšší úrovně, které nejsou vnořené v jiných typech, může mít pouze `internal` nebo `public` usnadnění.</span><span class="sxs-lookup"><span data-stu-id="58f0c-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="58f0c-118">Je výchozí usnadnění pro tyto typy `internal`.</span><span class="sxs-lookup"><span data-stu-id="58f0c-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="58f0c-119">Vnořené typy, které jsou členy jiné typy, můžete mít deklarovat přístupnosti, které je uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="58f0c-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="58f0c-120">Členové</span><span class="sxs-lookup"><span data-stu-id="58f0c-120">Members of</span></span>|<span data-ttu-id="58f0c-121">Výchozí člen pro usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="58f0c-121">Default member accessibility</span></span>|<span data-ttu-id="58f0c-122">Povolené deklarované usnadnění člena</span><span class="sxs-lookup"><span data-stu-id="58f0c-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="58f0c-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="58f0c-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="58f0c-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="58f0c-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="58f0c-125">Usnadnění vnořeného typu závisí na jeho [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md), což je dáno tím deklarované usnadnění člena a doména přístupnosti okamžitě nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="58f0c-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="58f0c-126">Doména přístupnosti vnořeného typu však nesmí překročit u nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="58f0c-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="58f0c-127">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="58f0c-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="58f0c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="58f0c-128">See Also</span></span>  
 [<span data-ttu-id="58f0c-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="58f0c-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="58f0c-130">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="58f0c-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="58f0c-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="58f0c-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="58f0c-132">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="58f0c-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="58f0c-133">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="58f0c-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="58f0c-134">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="58f0c-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="58f0c-135">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="58f0c-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="58f0c-136">veřejné</span><span class="sxs-lookup"><span data-stu-id="58f0c-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="58f0c-137">privátní</span><span class="sxs-lookup"><span data-stu-id="58f0c-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="58f0c-138">chráněný</span><span class="sxs-lookup"><span data-stu-id="58f0c-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="58f0c-139">interní</span><span class="sxs-lookup"><span data-stu-id="58f0c-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
