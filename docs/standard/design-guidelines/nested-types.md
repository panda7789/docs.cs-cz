---
title: Vnořené typy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: KrzysztofCwalina
ms.openlocfilehash: 22c14d05105154ff642cb8a44eda8e7c5d0575e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559538"
---
# <a name="nested-types"></a><span data-ttu-id="4908b-102">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="4908b-102">Nested Types</span></span>
<span data-ttu-id="4908b-103">Vnořený typ je typ definovaný v rámci jiného typu, která se nazývá nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="4908b-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="4908b-104">Vnořený typ má přístup na všechny členy jeho nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="4908b-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="4908b-105">Například má přístup k privátním položkám definované nadřazeného typu a chráněné pole definovaná ve všech nadřazených členů nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="4908b-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="4908b-106">Obecně platí vnořené typy by měly používat střídmě.</span><span class="sxs-lookup"><span data-stu-id="4908b-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="4908b-107">Existuje několik důvodů.</span><span class="sxs-lookup"><span data-stu-id="4908b-107">There are several reasons for this.</span></span> <span data-ttu-id="4908b-108">Někteří vývojáři nejsou plně seznámení s konceptem.</span><span class="sxs-lookup"><span data-stu-id="4908b-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="4908b-109">Tyto vývojáře, například mít problémy se syntaxí File://Server.Fabrikam.com/SD deklarování proměnných vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="4908b-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="4908b-110">Vnořené typy jsou také velmi úzce svázány s jejich nadřazené typy a jako taková nejsou vhodné být obecné typy.</span><span class="sxs-lookup"><span data-stu-id="4908b-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="4908b-111">Vnořené typy jsou nejvhodnější pro modelování podrobnosti implementace jejich nadřazené typy.</span><span class="sxs-lookup"><span data-stu-id="4908b-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="4908b-112">Koncový uživatel by měl mít jen zřídka pro deklarování proměnných vnořeného typu a téměř nikdy by měl mít explicitně vytvořit instanci vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="4908b-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="4908b-113">Například čítače výčtu kolekce může být vnořený typ této kolekce.</span><span class="sxs-lookup"><span data-stu-id="4908b-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="4908b-114">Instance čítače se obvykle vytvářejí pomocí jejich nadřazených typů a protože mnoho jazyky podporují příkaz foreach, enumerátor proměnné zřídka musí deklarovat koncovým uživatelem.</span><span class="sxs-lookup"><span data-stu-id="4908b-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="4908b-115">**✓ DO** použití vnořené typy vztah mezi vnořené typy a jeho vnější typ tak, aby člen usnadnění sémantika je žádoucí.</span><span class="sxs-lookup"><span data-stu-id="4908b-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="4908b-116">**X DO NOT** použití veřejného vnořené typy jako logické seskupení vytvořit; pomocí oborů názvů pro tuto.</span><span class="sxs-lookup"><span data-stu-id="4908b-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="4908b-117">**X AVOID** veřejně vystaven vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="4908b-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="4908b-118">Jedinou výjimkou je, pokud proměnné vnořeného typu potřeba deklarovat pouze ve výjimečných případech, jako je například vytvoření podtřídy nebo jiné scénáře rozšířená přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="4908b-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="4908b-119">**X DO NOT** použijte vnořené typy, pokud typ je pravděpodobně bude odkazovat mimo nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="4908b-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="4908b-120">Například výčet předaný metodě definované třídy nesmí být definována jako vnořený typ ve třídě.</span><span class="sxs-lookup"><span data-stu-id="4908b-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="4908b-121">**X DO NOT** použít vnořené typy, pokud je nutné vytvořit instanci kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="4908b-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="4908b-122">Pokud typ nemá veřejný konstruktor, ji by měl pravděpodobně není vnořit.</span><span class="sxs-lookup"><span data-stu-id="4908b-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="4908b-123">Pokud můžete vytvořit instanci typu, který zdá se, že označuje typ má místo v rámci sama o sobě (můžete ji vytvořit, pracujete s ním a zničit bez někdy použití vnějšího typu) a proto by neměl být vnořený.</span><span class="sxs-lookup"><span data-stu-id="4908b-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="4908b-124">Vnitřní typy by neměly znovu použít široce mimo vnější typ bez jakékoli relace jednání do vnějšího typu.</span><span class="sxs-lookup"><span data-stu-id="4908b-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="4908b-125">**X DO NOT** definovat vnořené typy jako člen rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4908b-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="4908b-126">Řadu jiných jazyků nepodporují tato konstrukce.</span><span class="sxs-lookup"><span data-stu-id="4908b-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="4908b-127">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4908b-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4908b-128">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="4908b-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4908b-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4908b-129">See also</span></span>

- [<span data-ttu-id="4908b-130">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="4908b-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="4908b-131">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="4908b-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
