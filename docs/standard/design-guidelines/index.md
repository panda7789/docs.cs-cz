---
title: Pokyny k návrhu architektury
description: Pokyny k návrhu knihoven, které šíří a komunikují s .NET, najdete v tématu věnovaném návrhům rozhraní API pro zajištění konzistence rozhraní API a snadného použití.
titleSuffix: ''
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 17998adb1d18579f6763a80a82944e742e284e4e
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769064"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="140d7-103">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="140d7-103">Framework Design Guidelines</span></span>
<span data-ttu-id="140d7-104">V této části najdete pokyny pro návrh knihoven, které rozšíří a komunikují s .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="140d7-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="140d7-105">Cílem je pomáhat Návrháři knihovny zajistit konzistenci rozhraní API a snadné použití poskytnutím jednotného programovacího modelu, který je nezávislý na programovacím jazyku používaném pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="140d7-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="140d7-106">Při vývoji tříd a komponent, které .NET Framework rozšiřuje, doporučujeme postupovat podle těchto pokynů k návrhu.</span><span class="sxs-lookup"><span data-stu-id="140d7-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="140d7-107">Nekonzistentní návrh knihovny nepříznivě ovlivňuje produktivitu vývojářů a nedoporučuje přijetí.</span><span class="sxs-lookup"><span data-stu-id="140d7-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="140d7-108">Pokyny jsou uspořádané jako jednoduchá doporučení s předponami,, `Do` `Consider` `Avoid` a `Do not` .</span><span class="sxs-lookup"><span data-stu-id="140d7-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="140d7-109">Tyto pokyny jsou určeny k tomu, aby Návrháři knihoven tříd pochopili kompromisy mezi různými řešeními.</span><span class="sxs-lookup"><span data-stu-id="140d7-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="140d7-110">Můžou nastat situace, kdy dobrý návrh knihovny vyžaduje, abyste ponarušili tyto pokyny k návrhu.</span><span class="sxs-lookup"><span data-stu-id="140d7-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="140d7-111">Takové případy by měly být vzácné a je důležité, abyste měli jasný a přesvědčivý důvod pro vaše rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="140d7-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="140d7-112">Tyto pokyny jsou uvedené v *pokynech pro návrh Book Framework: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice*, Krzysztof Cwalina a Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="140d7-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="140d7-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="140d7-113">In This Section</span></span>  
 [<span data-ttu-id="140d7-114">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="140d7-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="140d7-115">Poskytuje pokyny pro pojmenování sestavení, oborů názvů, typů a členů v knihovnách tříd.</span><span class="sxs-lookup"><span data-stu-id="140d7-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="140d7-116">Pokyny pro návrh typů</span><span class="sxs-lookup"><span data-stu-id="140d7-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="140d7-117">Poskytuje pokyny pro použití statických a abstraktních tříd, rozhraní, výčtů, struktur a dalších typů.</span><span class="sxs-lookup"><span data-stu-id="140d7-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="140d7-118">Pokyny pro návrh členů</span><span class="sxs-lookup"><span data-stu-id="140d7-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="140d7-119">Poskytuje pokyny pro návrh a používání vlastností, metod, konstruktorů, polí, událostí, operátorů a parametrů.</span><span class="sxs-lookup"><span data-stu-id="140d7-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="140d7-120">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="140d7-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="140d7-121">Popisuje mechanismy rozšiřitelnosti, jako je například použití podtříd, používání událostí, virtuálních členů a zpětných volání, a vysvětluje, jak zvolit mechanismy, které nejlépe vyhovují požadavkům vašeho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="140d7-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="140d7-122">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="140d7-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="140d7-123">Popisuje pokyny návrhu pro návrh, vyvolání a zachycení výjimek.</span><span class="sxs-lookup"><span data-stu-id="140d7-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="140d7-124">Pokyny k použití</span><span class="sxs-lookup"><span data-stu-id="140d7-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="140d7-125">Popisuje pokyny pro použití běžných typů, jako jsou pole, atributy a kolekce, podpora serializace a přetížení operátorů rovnosti.</span><span class="sxs-lookup"><span data-stu-id="140d7-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="140d7-126">Běžné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="140d7-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="140d7-127">Poskytuje pokyny pro výběr a implementaci vlastností závislosti.</span><span class="sxs-lookup"><span data-stu-id="140d7-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="140d7-128">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="140d7-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="140d7-129">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="140d7-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="140d7-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="140d7-130">See also</span></span>

- [<span data-ttu-id="140d7-131">Přehled</span><span class="sxs-lookup"><span data-stu-id="140d7-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="140d7-132">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="140d7-132">Development Guide</span></span>](../../framework/development-guide.md)
