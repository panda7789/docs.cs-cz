---
title: "Vnořené typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 389ba73c4509f41f6c2cf86363e59ea720eb3c9f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="nested-types"></a><span data-ttu-id="b292a-102">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="b292a-102">Nested Types</span></span>
<span data-ttu-id="b292a-103">Vnořené typy je typem definovaným v rámci oboru jiného typu, který se nazývá nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="b292a-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="b292a-104">Vnořené typy má přístup do všech členů jeho nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="b292a-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="b292a-105">Například má přístup k privátním pole definovaná v nadřazených typů a chráněné polí definovaných ve všech nadřazených členů nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="b292a-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="b292a-106">Obecně platí vnořené typy měli šetřit.</span><span class="sxs-lookup"><span data-stu-id="b292a-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="b292a-107">Tady je několik důvodů pro tento.</span><span class="sxs-lookup"><span data-stu-id="b292a-107">There are several reasons for this.</span></span> <span data-ttu-id="b292a-108">Někteří vývojáři se plně s koncept.</span><span class="sxs-lookup"><span data-stu-id="b292a-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="b292a-109">Tyto vývojáři může například máte problémy s syntaxe deklarace proměnné vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="b292a-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="b292a-110">Vnořené typy jsou také velmi úzce spojeny s jejich nadřazených typů a jako takový nejsou vhodné jako typy pro obecné účely.</span><span class="sxs-lookup"><span data-stu-id="b292a-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="b292a-111">Vnořené typy jsou nejvhodnější pro modelování podrobnosti implementace jejich nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="b292a-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="b292a-112">Koncový uživatel by měl obvykle nemusí deklarujte proměnné vnořené typy a téměř žádné musí mít explicitně instance vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="b292a-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="b292a-113">Enumerátor kolekce může být například vnořené typ této kolekce.</span><span class="sxs-lookup"><span data-stu-id="b292a-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="b292a-114">Výčty jsou obvykle mohl vytvořit jeho instanci názvy jejich nadřazených typů a mnoha jazycích nepodporují příkazu foreach, enumerátor proměnné zřídka mají deklarovat koncovým uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b292a-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="b292a-115">**PROVEĎTE ✓** použití vnořené typy vztah mezi vnořené typy a jeho vnější typ tak, aby člen usnadnění sémantika je žádoucí.</span><span class="sxs-lookup"><span data-stu-id="b292a-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="b292a-116">**X nesmí** použití veřejného vnořené typy jako logické seskupení vytvořit; pomocí oborů názvů pro tuto.</span><span class="sxs-lookup"><span data-stu-id="b292a-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="b292a-117">**X nepoužívejte** veřejně vystaven vnořené typy.</span><span class="sxs-lookup"><span data-stu-id="b292a-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="b292a-118">Jedinou výjimkou je, pokud proměnné vnořené typy potřeba deklarovat pouze ve výjimečných případech, například vytvoření podtřídy či jiné scénáře vlastní nastavení.</span><span class="sxs-lookup"><span data-stu-id="b292a-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="b292a-119">**X nesmí** použijte vnořené typy, pokud typ je pravděpodobně bude odkazovat mimo nadřazeného typu.</span><span class="sxs-lookup"><span data-stu-id="b292a-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="b292a-120">Například výčet předaný metodě definovaný pro třídu nesmí být definována jako typ vnořené v třídě.</span><span class="sxs-lookup"><span data-stu-id="b292a-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="b292a-121">**X nesmí** použít vnořené typy, pokud je nutné vytvořit instanci kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="b292a-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="b292a-122">Pokud typ má konstruktor public, ho měli pravděpodobně není nelze vnořit.</span><span class="sxs-lookup"><span data-stu-id="b292a-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="b292a-123">Pokud typ se dá vytvořit instance, která zdá se, že k označení, typ je na místě v rozhraní framework svoje vlastní (můžete ji vytvořit, s ním pracovat a zrušení bez někdy pomocí vnější typu) a proto by neměl být vnořený.</span><span class="sxs-lookup"><span data-stu-id="b292a-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="b292a-124">Vnitřní typy by neměly znovu široce mimo vnější typu bez žádný vztah jakékoli vnější typu.</span><span class="sxs-lookup"><span data-stu-id="b292a-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="b292a-125">**X nesmí** definovat vnořené typy jako člen rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b292a-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="b292a-126">Mnoho jazyků nepodporují takové konstrukce.</span><span class="sxs-lookup"><span data-stu-id="b292a-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="b292a-127">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="b292a-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b292a-128">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="b292a-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b292a-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="b292a-129">See Also</span></span>  
 [<span data-ttu-id="b292a-130">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="b292a-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="b292a-131">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="b292a-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
