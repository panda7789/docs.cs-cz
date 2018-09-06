---
title: Pokyny k návrhu typu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7fb9964d0e542c0937c55ae65bd88b3f7149fa8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036022"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="6820c-102">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="6820c-102">Type Design Guidelines</span></span>
<span data-ttu-id="6820c-103">Z pohledu CLR existují jenom dvě kategorie typů – typy odkazu a typy hodnot, ale pro účely diskuse o návrhu rozhraní framework, jsme typy rozdělit do více logických skupin, každou s vlastní pravidla konkrétního návrhu.</span><span class="sxs-lookup"><span data-stu-id="6820c-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="6820c-104">Třídy jsou obecné případ odkazových typů.</span><span class="sxs-lookup"><span data-stu-id="6820c-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="6820c-105">Tvoří hromadné typy ve většině platforem.</span><span class="sxs-lookup"><span data-stu-id="6820c-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="6820c-106">Třídy je splatná jejich oblíbenosti bohaté sady objektově orientovaných vlastností, které podporují a jejich obecné použitelnosti.</span><span class="sxs-lookup"><span data-stu-id="6820c-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="6820c-107">Základní třídy a abstraktní třídy jsou speciální logických skupin souvisejících do rozšíření.</span><span class="sxs-lookup"><span data-stu-id="6820c-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="6820c-108">Rozhraní jsou typy, které je možné implementovat pomocí odkazové typy a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="6820c-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="6820c-109">Proto mohou sloužit jako kořeny hierarchie polymorfní typy odkazů a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="6820c-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="6820c-110">Kromě toho rozhraní umožňuje simulovat vícenásobná dědičnost, což není podporováno nativně modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="6820c-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="6820c-111">Struktury jsou obecném případě typy hodnot a by se mělo vyhradit pro malé, jednoduché typy, podobně jako primitiva jazyka.</span><span class="sxs-lookup"><span data-stu-id="6820c-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="6820c-112">Výčty představují zvláštní případ typů hodnot, které slouží k definování krátký sady hodnot, například dny v týdnu, barvy konzoly a tak dále.</span><span class="sxs-lookup"><span data-stu-id="6820c-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="6820c-113">Statické třídy jsou typy, které má být kontejnery pro statické členy.</span><span class="sxs-lookup"><span data-stu-id="6820c-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="6820c-114">Běžně se používají k poskytování klávesové zkratky pro jiné operace.</span><span class="sxs-lookup"><span data-stu-id="6820c-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="6820c-115">Delegáty, výjimky, atributy, pole a kolekce jsou všechny speciální případy typy odkazů, které jsou určené pro konkrétní použití, a pokyny pro jejich návrhu a využití jsou jinde popsaných v této příručce.</span><span class="sxs-lookup"><span data-stu-id="6820c-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="6820c-116">**✓ DO** zajistěte, aby byl každý typ dobře definované sadě souvisejících členů, nejen náhodné kolekce funkcí, které nejsou.</span><span class="sxs-lookup"><span data-stu-id="6820c-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6820c-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="6820c-117">In This Section</span></span>  
 [<span data-ttu-id="6820c-118">Volba mezi třídou a strukturou</span><span class="sxs-lookup"><span data-stu-id="6820c-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="6820c-119">Návrh abstraktní třídy</span><span class="sxs-lookup"><span data-stu-id="6820c-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="6820c-120">Návrh statické třídy</span><span class="sxs-lookup"><span data-stu-id="6820c-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="6820c-121">Návrh rozhraní</span><span class="sxs-lookup"><span data-stu-id="6820c-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="6820c-122">Návrh struktury</span><span class="sxs-lookup"><span data-stu-id="6820c-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="6820c-123">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="6820c-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="6820c-124">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="6820c-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="6820c-125">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="6820c-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="6820c-126">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="6820c-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6820c-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6820c-127">See also</span></span>

- [<span data-ttu-id="6820c-128">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="6820c-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
