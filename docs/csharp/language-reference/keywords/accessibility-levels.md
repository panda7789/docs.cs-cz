---
title: Úrovně přístupnosti (Referenční dokumentace jazyka C#)
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 4679fd2564454e7f1ade5cb4813729b65f433012
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44046564"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="34b6a-102">Úrovně přístupnosti (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="34b6a-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="34b6a-103">Používat modifikátory přístupu `public`, `protected`, `internal`, nebo `private`, chcete-li určit jednu z následujících úrovní deklarovaná přístupnost členů.</span><span class="sxs-lookup"><span data-stu-id="34b6a-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="34b6a-104">Deklarovaná přístupnost</span><span class="sxs-lookup"><span data-stu-id="34b6a-104">Declared accessibility</span></span>|<span data-ttu-id="34b6a-105">Význam</span><span class="sxs-lookup"><span data-stu-id="34b6a-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="34b6a-106">Přístup není omezený.</span><span class="sxs-lookup"><span data-stu-id="34b6a-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="34b6a-107">Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="34b6a-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="34b6a-108">Přístup je omezený na aktuální sestavení.</span><span class="sxs-lookup"><span data-stu-id="34b6a-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="34b6a-109">Přístup je omezený na aktuální sestavení nebo typy odvozené od třídy obsahující.</span><span class="sxs-lookup"><span data-stu-id="34b6a-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="34b6a-110">Přístup je omezený na nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="34b6a-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="34b6a-111">Přístup je omezený na obsahující třídu nebo typy odvozené od třídy obsahující v rámci aktuálního sestavení.</span><span class="sxs-lookup"><span data-stu-id="34b6a-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="34b6a-112">Dostupné od verze C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="34b6a-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="34b6a-113">Modifikátor přístupu pouze jeden je povolený pro člen nebo typ, s výjimkou při použití `protected internal` nebo `private protected` kombinace.</span><span class="sxs-lookup"><span data-stu-id="34b6a-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="34b6a-114">Modifikátory přístupu nejsou povoleny u oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="34b6a-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="34b6a-115">Obory názvů nemá žádné omezení přístupu.</span><span class="sxs-lookup"><span data-stu-id="34b6a-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="34b6a-116">V závislosti na kontextu, ve kterém dochází k deklaraci člena jsou povoleny pouze určité deklarované přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="34b6a-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="34b6a-117">Pokud v deklaraci člena není zadán žádný modifikátor přístupu, použije se výchozí dostupnost.</span><span class="sxs-lookup"><span data-stu-id="34b6a-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="34b6a-118">Nejvyšší úrovně typy, které nejsou vnořené v jiných typech, může mít pouze `internal` nebo `public` usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="34b6a-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="34b6a-119">Výchozí dostupnost pro tyto typy je `internal`.</span><span class="sxs-lookup"><span data-stu-id="34b6a-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="34b6a-120">Vnořené typy, které jsou členy ostatních typů, mohou být deklarovány přístupnosti jak je uvedeno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="34b6a-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="34b6a-121">Členové</span><span class="sxs-lookup"><span data-stu-id="34b6a-121">Members of</span></span>|<span data-ttu-id="34b6a-122">Výchozí člen dostupnost</span><span class="sxs-lookup"><span data-stu-id="34b6a-122">Default member accessibility</span></span>|<span data-ttu-id="34b6a-123">Povolené deklarovaná přístupnost člena</span><span class="sxs-lookup"><span data-stu-id="34b6a-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="34b6a-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="34b6a-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="34b6a-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="34b6a-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="34b6a-126">Přístupnost vnořeného typu závisí na jeho [doména přístupnosti](../../../csharp/language-reference/keywords/accessibility-domain.md), které je určeno deklarovanou přístupností člena a doménou přístupnosti bezprostředně nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="34b6a-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="34b6a-127">Doména přístupnosti vnořeného typu však nesmí přesáhnout přístupnost nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="34b6a-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="34b6a-128">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34b6a-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="34b6a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="34b6a-129">See Also</span></span>  
- [<span data-ttu-id="34b6a-130">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34b6a-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="34b6a-131">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="34b6a-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="34b6a-132">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="34b6a-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="34b6a-133">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="34b6a-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="34b6a-134">Doména přístupnosti</span><span class="sxs-lookup"><span data-stu-id="34b6a-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
- [<span data-ttu-id="34b6a-135">Omezení používání úrovní přístupu</span><span class="sxs-lookup"><span data-stu-id="34b6a-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
- [<span data-ttu-id="34b6a-136">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="34b6a-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="34b6a-137">public</span><span class="sxs-lookup"><span data-stu-id="34b6a-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="34b6a-138">private</span><span class="sxs-lookup"><span data-stu-id="34b6a-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="34b6a-139">protected</span><span class="sxs-lookup"><span data-stu-id="34b6a-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
- [<span data-ttu-id="34b6a-140">internal</span><span class="sxs-lookup"><span data-stu-id="34b6a-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
