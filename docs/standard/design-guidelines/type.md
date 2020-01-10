---
title: Pokyny k návrhu typu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709020"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="a825f-102">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="a825f-102">Type Design Guidelines</span></span>
<span data-ttu-id="a825f-103">Z perspektivy CLR existují pouze dvě kategorie typů – typy odkazů a typy hodnot – ale pro účely diskuze o návrhu rozhraní rozdělíme typy do více logických skupin, z nichž každá má konkrétní pravidla návrhu.</span><span class="sxs-lookup"><span data-stu-id="a825f-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="a825f-104">Třídy jsou obecné velikosti typů odkazů.</span><span class="sxs-lookup"><span data-stu-id="a825f-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="a825f-105">Tvoří velkou část typů ve většině platforem.</span><span class="sxs-lookup"><span data-stu-id="a825f-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="a825f-106">Třídy odtřídí své oblíbenosti na bohatou sadu objektově orientovaných funkcí, které podporují, a jejich obecné použitelnosti.</span><span class="sxs-lookup"><span data-stu-id="a825f-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="a825f-107">Základní třídy a abstraktní třídy jsou speciální logické skupiny, které souvisejí s rozšiřitelnou.</span><span class="sxs-lookup"><span data-stu-id="a825f-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="a825f-108">Rozhraní jsou typy, které mohou být implementovány oběma typy odkazu a typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="a825f-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="a825f-109">Mohou proto sloužit jako kořeny polymorfních hierarchií typů odkazů a typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="a825f-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="a825f-110">Kromě toho lze rozhraní použít k simulaci vícenásobné dědičnosti, která není nativně podporována modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="a825f-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="a825f-111">Struktury jsou obecné typy hodnot a měly by být rezervovány pro malé, jednoduché typy, podobně jako jazykové primitivy.</span><span class="sxs-lookup"><span data-stu-id="a825f-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="a825f-112">Výčty jsou zvláštní případ hodnotových typů, které slouží k definování krátkých sad hodnot, například dnů v týdnu, barev konzoly atd.</span><span class="sxs-lookup"><span data-stu-id="a825f-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="a825f-113">Statické třídy jsou typy, které mají být kontejnery pro statické členy.</span><span class="sxs-lookup"><span data-stu-id="a825f-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="a825f-114">Obvykle se používají k poskytnutí zástupců pro jiné operace.</span><span class="sxs-lookup"><span data-stu-id="a825f-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="a825f-115">Delegáti, výjimky, atributy, pole a kolekce jsou všechny zvláštní případy odkazových typů určených pro konkrétní použití a pokyny pro jejich návrh a použití jsou popsány jinde v této knize.</span><span class="sxs-lookup"><span data-stu-id="a825f-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="a825f-116">**✓ DO** zajistěte, aby byl každý typ dobře definované sadě souvisejících členů, nejen náhodné kolekce funkcí, které nejsou.</span><span class="sxs-lookup"><span data-stu-id="a825f-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a825f-117">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a825f-117">In This Section</span></span>  
 [<span data-ttu-id="a825f-118">Volba mezi třídou a strukturou</span><span class="sxs-lookup"><span data-stu-id="a825f-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="a825f-119">Návrh abstraktní třídy</span><span class="sxs-lookup"><span data-stu-id="a825f-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="a825f-120">Návrh statické třídy</span><span class="sxs-lookup"><span data-stu-id="a825f-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="a825f-121">Návrh rozhraní</span><span class="sxs-lookup"><span data-stu-id="a825f-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="a825f-122">Návrh struktury</span><span class="sxs-lookup"><span data-stu-id="a825f-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="a825f-123">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="a825f-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="a825f-124">Vnořené typy</span><span class="sxs-lookup"><span data-stu-id="a825f-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="a825f-125">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="a825f-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a825f-126">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="a825f-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a825f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a825f-127">See also</span></span>

- [<span data-ttu-id="a825f-128">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="a825f-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
