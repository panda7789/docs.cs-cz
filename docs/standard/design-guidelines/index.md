---
title: "Pokyny k\_návrhu architektury"
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
  - 'libraries, .NET Framework class library'
  - 'class library design guidelines [.NET Framework], about'
  - 'class library design guidelines [.NET Framework]'
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
author: KrzysztofCwalina
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="43022-102">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="43022-102">Framework Design Guidelines</span></span>
<span data-ttu-id="43022-103">Tato část obsahuje pokyny pro návrh knihoven, které rozšiřují a pracovat s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43022-103">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="43022-104">Cílem je pomoct knihovny návrhářů tím, že poskytuje jednotný programovací model, který je nezávislý na programovací jazyk se používá pro vývoj pro zajištění konzistence rozhraní API a snadné použití.</span><span class="sxs-lookup"><span data-stu-id="43022-104">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="43022-105">Doporučujeme postupovat podle následujících pokynů návrhu, při vytváření tříd a komponent, které rozšiřují rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43022-105">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="43022-106">Návrh nekonzistentní knihovny nepříznivě má vliv na produktivitu vývojářů a odrazuje od přijetí.</span><span class="sxs-lookup"><span data-stu-id="43022-106">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="43022-107">Pokyny jsou uspořádané jako jednoduchý doporučení předponu podmínky `Do`, `Consider`, `Avoid`, a `Do not`.</span><span class="sxs-lookup"><span data-stu-id="43022-107">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="43022-108">Tyto pokyny jsou určeny k pomohou návrhářům tříd knihovny pochopit kompromisy mezi různými řešeními.</span><span class="sxs-lookup"><span data-stu-id="43022-108">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="43022-109">Můžou nastat situace, kdy návrh dobrý knihovna vyžaduje, aby že porušují tyto pokyny k návrhu.</span><span class="sxs-lookup"><span data-stu-id="43022-109">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="43022-110">Takové případy by měl být vzácné a je důležité, abyste měli vymazat a poutavé důvod svého rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="43022-110">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="43022-111">Tyto pokyny jsou výňatkem z knihy *pokyny k návrhu architektury: Konvence, Idiomy a vzory pro knihovny opakovaně použitelných .NET, 2nd Edition*, Krzysztof Cwalina a Brad Abrams.</span><span class="sxs-lookup"><span data-stu-id="43022-111">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43022-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="43022-112">In This Section</span></span>  
 [<span data-ttu-id="43022-113">Pokyny pro pojmenování</span><span class="sxs-lookup"><span data-stu-id="43022-113">Naming Guidelines</span></span>](../../../docs/standard/design-guidelines/naming-guidelines.md)  
 <span data-ttu-id="43022-114">Obsahuje pokyny pro pojmenování sestavení, oborů názvů, typy a členy v knihovnách tříd.</span><span class="sxs-lookup"><span data-stu-id="43022-114">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="43022-115">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="43022-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 <span data-ttu-id="43022-116">Poskytuje pokyny pro používání statických a abstraktní třídy, rozhraní, výčty, struktury a ostatní typy.</span><span class="sxs-lookup"><span data-stu-id="43022-116">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="43022-117">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="43022-117">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 <span data-ttu-id="43022-118">Obsahuje pokyny pro návrh a pomocí vlastnosti, metody, konstruktory, pole, události, operátory a parametry.</span><span class="sxs-lookup"><span data-stu-id="43022-118">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="43022-119">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="43022-119">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 <span data-ttu-id="43022-120">Popisuje rozšíření mechanismy, jako je vytváření podtříd, události, virtuální členy a zpětná volání a vysvětluje, jak zvolit mechanismy, které nejlépe splňovat požadavky na vaše architektura.</span><span class="sxs-lookup"><span data-stu-id="43022-120">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="43022-121">Pokyny k návrhu pro výjimky</span><span class="sxs-lookup"><span data-stu-id="43022-121">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)  
 <span data-ttu-id="43022-122">Popisuje pokyny k návrhu pro navrhování, vyvolání a zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="43022-122">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="43022-123">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="43022-123">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)  
 <span data-ttu-id="43022-124">Popisuje pokyny pro běžné typy, jako je například pole, atributy a kolekce pomocí, podpora serializace a operátory rovnosti přetížení.</span><span class="sxs-lookup"><span data-stu-id="43022-124">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="43022-125">Obecné vzory návrhu</span><span class="sxs-lookup"><span data-stu-id="43022-125">Common Design Patterns</span></span>](../../../docs/standard/design-guidelines/common-design-patterns.md)  
 <span data-ttu-id="43022-126">Obsahuje pokyny pro výběr a implementace vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="43022-126">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="43022-127">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="43022-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="43022-128">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="43022-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43022-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43022-129">See also</span></span>

- [<span data-ttu-id="43022-130">Přehled</span><span class="sxs-lookup"><span data-stu-id="43022-130">Overview</span></span>](../../../docs/framework/get-started/overview.md)
- [<span data-ttu-id="43022-131">Průvodce vývojem</span><span class="sxs-lookup"><span data-stu-id="43022-131">Development Guide</span></span>](../../../docs/framework/development-guide.md)
