---
title: "Typ pokynů pro návrh"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2b24a934285f88386daa764c5b28bd82cf5d39a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-design-guidelines"></a><span data-ttu-id="30f3d-102">Typ pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="30f3d-102">Type Design Guidelines</span></span>
<span data-ttu-id="30f3d-103">Z pohledu CLR existují pouze dvě kategorie typů – reference a hodnotové typy – ale pro účely diskuze o návrhu framework, jsme typy rozdělit do více logických skupin, každou s vlastní pravidla konkrétní návrhu.</span><span class="sxs-lookup"><span data-stu-id="30f3d-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="30f3d-104">Třídy jsou obecné malá odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="30f3d-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="30f3d-105">Tvoří hromadné typů ve většině architektury.</span><span class="sxs-lookup"><span data-stu-id="30f3d-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="30f3d-106">Třídy dlužíte jejich oblíbenosti bohaté sada funkce, které podporují a jejich obecné použitelnosti.</span><span class="sxs-lookup"><span data-stu-id="30f3d-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="30f3d-107">Základní třídy a abstraktní třídy jsou speciální logické skupiny související s rozšíření.</span><span class="sxs-lookup"><span data-stu-id="30f3d-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="30f3d-108">Rozhraní jsou typy, které se dají implementovat odkazové typy a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="30f3d-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="30f3d-109">Proto se může sloužit jako kořeny polymorfní hierarchií odkazové typy a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="30f3d-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="30f3d-110">Kromě toho rozhraní slouží k simulaci vícenásobná dědičnost, což není podporováno nativně modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="30f3d-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="30f3d-111">Struktury jsou obecné případ typů hodnot a by se mělo vyhradit pro malé, jednoduché typy, podobně jako primitiva jazyka.</span><span class="sxs-lookup"><span data-stu-id="30f3d-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="30f3d-112">Výčty jsou ve speciálním případě typů hodnot se používá k definování krátké sady hodnot, například dny v týdnu, barvy konzoly a tak dále.</span><span class="sxs-lookup"><span data-stu-id="30f3d-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="30f3d-113">Statické třídy jsou typy by měla být kontejnery pro statické členy.</span><span class="sxs-lookup"><span data-stu-id="30f3d-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="30f3d-114">Běžně se používají k poskytování zástupce jiné operace.</span><span class="sxs-lookup"><span data-stu-id="30f3d-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="30f3d-115">Delegáti, výjimky, atributy, pole a kolekce jsou všechny zvláštních případech odkazové typy určené pro konkrétní účely a pokyny pro jejich využití a návrhu jsou popsané jinde v této příručce.</span><span class="sxs-lookup"><span data-stu-id="30f3d-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="30f3d-116">**PROVEĎTE ✓** zajistěte, aby byl každý typ dobře definované sadě souvisejících členů, nejen náhodné kolekce funkcí, které nejsou.</span><span class="sxs-lookup"><span data-stu-id="30f3d-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30f3d-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="30f3d-117">In This Section</span></span>  
 [<span data-ttu-id="30f3d-118">Volba mezi třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="30f3d-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="30f3d-119">Abstraktní třída návrhu</span><span class="sxs-lookup"><span data-stu-id="30f3d-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="30f3d-120">Statická třída návrhu</span><span class="sxs-lookup"><span data-stu-id="30f3d-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="30f3d-121">Rozhraní návrhu</span><span class="sxs-lookup"><span data-stu-id="30f3d-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="30f3d-122">Struktura návrhu</span><span class="sxs-lookup"><span data-stu-id="30f3d-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="30f3d-123">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="30f3d-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="30f3d-124">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="30f3d-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="30f3d-125">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="30f3d-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="30f3d-126">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="30f3d-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f3d-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="30f3d-127">See Also</span></span>  
 [<span data-ttu-id="30f3d-128">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="30f3d-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
