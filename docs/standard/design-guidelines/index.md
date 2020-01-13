---
title: Pokyny k návrhu architektury
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 8abe64476a5d3d1319dfa30dd7a06dc2bb541a0f
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904617"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="4b574-102">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="4b574-102">Framework Design Guidelines</span></span>
<span data-ttu-id="4b574-103">V této části najdete pokyny pro návrh knihoven, které rozšíří a komunikují s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b574-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="4b574-104">Cílem je pomáhat Návrháři knihovny zajistit konzistenci rozhraní API a snadné použití poskytnutím jednotného programovacího modelu, který je nezávislý na programovacím jazyku používaném pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="4b574-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="4b574-105">Při vývoji tříd a komponent, které .NET Framework rozšiřuje, doporučujeme postupovat podle těchto pokynů k návrhu.</span><span class="sxs-lookup"><span data-stu-id="4b574-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="4b574-106">Nekonzistentní návrh knihovny nepříznivě ovlivňuje produktivitu vývojářů a nedoporučuje přijetí.</span><span class="sxs-lookup"><span data-stu-id="4b574-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="4b574-107">Pokyny jsou uspořádané jako jednoduchá doporučení s podmínkami `Do`, `Consider`, `Avoid`a `Do not`.</span><span class="sxs-lookup"><span data-stu-id="4b574-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="4b574-108">Tyto pokyny jsou určeny k tomu, aby Návrháři knihoven tříd pochopili kompromisy mezi různými řešeními.</span><span class="sxs-lookup"><span data-stu-id="4b574-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="4b574-109">Můžou nastat situace, kdy dobrý návrh knihovny vyžaduje, abyste ponarušili tyto pokyny k návrhu.</span><span class="sxs-lookup"><span data-stu-id="4b574-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="4b574-110">Takové případy by měly být vzácné a je důležité, abyste měli jasný a přesvědčivý důvod pro vaše rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="4b574-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="4b574-111">Tyto pokyny jsou uvedené v *pokynech pro návrh Book Framework: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice*, Krzysztof Cwalina a Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="4b574-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4b574-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4b574-112">In This Section</span></span>  
 [<span data-ttu-id="4b574-113">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="4b574-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="4b574-114">Poskytuje pokyny pro pojmenování sestavení, oborů názvů, typů a členů v knihovnách tříd.</span><span class="sxs-lookup"><span data-stu-id="4b574-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="4b574-115">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="4b574-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="4b574-116">Poskytuje pokyny pro použití statických a abstraktních tříd, rozhraní, výčtů, struktur a dalších typů.</span><span class="sxs-lookup"><span data-stu-id="4b574-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="4b574-117">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="4b574-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="4b574-118">Poskytuje pokyny pro návrh a používání vlastností, metod, konstruktorů, polí, událostí, operátorů a parametrů.</span><span class="sxs-lookup"><span data-stu-id="4b574-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="4b574-119">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="4b574-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="4b574-120">Popisuje mechanismy rozšiřitelnosti, jako je například použití podtříd, používání událostí, virtuálních členů a zpětných volání, a vysvětluje, jak zvolit mechanismy, které nejlépe vyhovují požadavkům vašeho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4b574-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="4b574-121">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="4b574-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="4b574-122">Popisuje pokyny návrhu pro návrh, vyvolání a zachycení výjimek.</span><span class="sxs-lookup"><span data-stu-id="4b574-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="4b574-123">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="4b574-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="4b574-124">Popisuje pokyny pro použití běžných typů, jako jsou pole, atributy a kolekce, podpora serializace a přetížení operátorů rovnosti.</span><span class="sxs-lookup"><span data-stu-id="4b574-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="4b574-125">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="4b574-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="4b574-126">Poskytuje pokyny pro výběr a implementaci vlastností závislosti.</span><span class="sxs-lookup"><span data-stu-id="4b574-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="4b574-127">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4b574-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4b574-128">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="4b574-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b574-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b574-129">See also</span></span>

- [<span data-ttu-id="4b574-130">Přehled</span><span class="sxs-lookup"><span data-stu-id="4b574-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="4b574-131">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="4b574-131">Development Guide</span></span>](../../../docs/framework/development-guide.md)
