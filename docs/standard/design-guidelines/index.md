---
title: Pokyny k návrhu architektury
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
caps.latest.revision: 14
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c48b3cbaae4155a894ba77263505b2ca85238427
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="50498-102">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="50498-102">Framework Design Guidelines</span></span>
<span data-ttu-id="50498-103">Tato část obsahuje pokyny pro návrh knihovny, které rozšiřují a interakci s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50498-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="50498-104">Cílem je pomoct knihovny Designer zajistit konzistentnost rozhraní API a snadné použití tím, že poskytuje jednotný programovací model, která je nezávislá programovací jazyk používaný pro vývoj.</span><span class="sxs-lookup"><span data-stu-id="50498-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="50498-105">Doporučujeme vám, postupujte podle těchto pokynů pro návrh, při vývoji třídy a součásti, které rozšiřují rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50498-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="50498-106">Návrh nekonzistentní knihovny nepříznivě ovlivní produktivita vývojářů a nedoporučuje přijetí.</span><span class="sxs-lookup"><span data-stu-id="50498-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="50498-107">Pokyny jsou uspořádána jako jednoduchý doporučení předponu s podmínkami `Do`, `Consider`, `Avoid`, a `Do not`.</span><span class="sxs-lookup"><span data-stu-id="50498-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="50498-108">Tyto pokyny jsou určeny k pomoci třídy knihovny Designer pochopit kompromis mezi různá řešení.</span><span class="sxs-lookup"><span data-stu-id="50498-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="50498-109">Můžou nastat situace, kdy dobrý knihovny návrhu vyžaduje způsobila porušení těchto pokynů pro návrh.</span><span class="sxs-lookup"><span data-stu-id="50498-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="50498-110">Takových případech by měl být výjimečná a je důležité, abyste měli vymazat a poutavých důvod pro vaše rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="50498-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="50498-111">Tyto pokyny jsou převzaty z knihy webových stránek *pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání*, Krzysztof Cwalina a Abrams Brada.</span><span class="sxs-lookup"><span data-stu-id="50498-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="50498-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="50498-112">In This Section</span></span>  
 [<span data-ttu-id="50498-113">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="50498-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="50498-114">Obsahuje pokyny pro pojmenování sestavení, obory názvů, typy a členy v knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="50498-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="50498-115">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="50498-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="50498-116">Poskytuje pokyny pro používání statických a abstraktní třídy, rozhraní, výčty, struktur a dalších typů.</span><span class="sxs-lookup"><span data-stu-id="50498-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="50498-117">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="50498-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="50498-118">Obsahuje pokyny pro návrh a pomocí vlastnosti, metody, konstruktory, pole, operátory, události a parametry.</span><span class="sxs-lookup"><span data-stu-id="50498-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="50498-119">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="50498-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="50498-120">Popisuje rozšiřitelnost mechanismy, jako je vytváření podtříd, pomocí události, virtuální členové a zpětná volání a vysvětluje, jak zvolit mechanismy, které nejlépe splňují požadavky vašeho framework.</span><span class="sxs-lookup"><span data-stu-id="50498-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="50498-121">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="50498-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="50498-122">Popisuje pokyny pro návrh pro navrhování, vyvolání a zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="50498-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="50498-123">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="50498-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="50498-124">Popisuje pokyny pro použití běžné typy, jako je například pole, atributy a kolekce, podporu serializace a přetížení operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="50498-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="50498-125">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="50498-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="50498-126">Obsahuje pokyny pro výběr a implementace vlastností závislostí a vzoru uvolnění.</span><span class="sxs-lookup"><span data-stu-id="50498-126">Provides guidelines for choosing and implementing dependency properties and the dispose pattern.</span></span>  
  
 <span data-ttu-id="50498-127">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="50498-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="50498-128">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="50498-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50498-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="50498-129">See Also</span></span>  
 [<span data-ttu-id="50498-130">Přehled</span><span class="sxs-lookup"><span data-stu-id="50498-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)  
 [<span data-ttu-id="50498-131">Plán pro rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="50498-131">Roadmap for the .NET Framework</span></span>](http://msdn.microsoft.com/library/0b46b7c6-9163-4f99-8e58-0d1ee7da8c67)  
 [<span data-ttu-id="50498-132">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="50498-132">Development Guide</span></span>](../../../docs/framework/development-guide.md)
