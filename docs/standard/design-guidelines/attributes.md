---
title: Atributy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: c7bbbda88bd2fddb235b9ae639848e08a452c913
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741783"
---
# <a name="attributes"></a><span data-ttu-id="5c14c-102">Atributy</span><span class="sxs-lookup"><span data-stu-id="5c14c-102">Attributes</span></span>
<span data-ttu-id="5c14c-103"><xref:System.Attribute?displayProperty=nameWithType> je základní třídou, která se používá k definování vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="5c14c-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>

 <span data-ttu-id="5c14c-104">Atributy jsou poznámky, které lze přidat do programovacích prvků, jako jsou sestavení, typy, členy a parametry.</span><span class="sxs-lookup"><span data-stu-id="5c14c-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="5c14c-105">Jsou uloženy v metadatech sestavení a lze k němu přistupovat za běhu pomocí rozhraní API pro reflexi.</span><span class="sxs-lookup"><span data-stu-id="5c14c-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="5c14c-106">Rozhraní například definuje <xref:System.ObsoleteAttribute>, které lze použít na typ nebo člena k označení toho, že typ nebo člen je zastaralý.</span><span class="sxs-lookup"><span data-stu-id="5c14c-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>

 <span data-ttu-id="5c14c-107">Atributy mohou mít jednu nebo více vlastností, které mohou obsahovat další data související s atributem.</span><span class="sxs-lookup"><span data-stu-id="5c14c-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="5c14c-108">`ObsoleteAttribute` například může získat další informace o vydané verzi, ve které se typ nebo člen nepoužívá, a popis nových rozhraní API nahrazující zastaralé rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5c14c-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>

 <span data-ttu-id="5c14c-109">Při použití atributu musí být zadány některé vlastnosti atributu.</span><span class="sxs-lookup"><span data-stu-id="5c14c-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="5c14c-110">Jsou označovány jako požadované vlastnosti nebo požadované argumenty, protože jsou reprezentovány jako parametry pozičního konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="5c14c-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="5c14c-111">Například vlastnost <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> <xref:System.Diagnostics.ConditionalAttribute> je požadovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5c14c-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>

 <span data-ttu-id="5c14c-112">Vlastnosti, které nemusí být nutně nutné zadat, když je atribut použit, se nazývají volitelné vlastnosti (nebo nepovinné argumenty).</span><span class="sxs-lookup"><span data-stu-id="5c14c-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="5c14c-113">Jsou reprezentovány nastavitelnou vlastností.</span><span class="sxs-lookup"><span data-stu-id="5c14c-113">They are represented by settable properties.</span></span> <span data-ttu-id="5c14c-114">Kompilátory poskytují speciální syntaxi pro nastavení těchto vlastností při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="5c14c-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="5c14c-115">Například vlastnost <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> představuje nepovinný argument.</span><span class="sxs-lookup"><span data-stu-id="5c14c-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>

 <span data-ttu-id="5c14c-116">✔️ vlastní třídy atributů Name s příponou "Attribute".</span><span class="sxs-lookup"><span data-stu-id="5c14c-116">✔️ DO name custom attribute classes with the suffix "Attribute."</span></span>

 <span data-ttu-id="5c14c-117">✔️ použít <xref:System.AttributeUsageAttribute> na vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="5c14c-117">✔️ DO apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>

 <span data-ttu-id="5c14c-118">✔️ poskytují nastavitelné vlastnosti pro volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="5c14c-118">✔️ DO provide settable properties for optional arguments.</span></span>

 <span data-ttu-id="5c14c-119">✔️ pro požadované argumenty Poskytněte vlastnosti jen pro získání.</span><span class="sxs-lookup"><span data-stu-id="5c14c-119">✔️ DO provide get-only properties for required arguments.</span></span>

 <span data-ttu-id="5c14c-120">✔️ poskytují parametry konstruktoru pro inicializaci vlastností, které odpovídají požadovaným argumentům.</span><span class="sxs-lookup"><span data-stu-id="5c14c-120">✔️ DO provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="5c14c-121">Každý parametr by měl mít stejný název (i v různých malých písmenech) jako odpovídající vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5c14c-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>

 <span data-ttu-id="5c14c-122">❌ se vyhnout poskytování parametrů konstruktoru pro inicializaci vlastností odpovídajících volitelným argumentům.</span><span class="sxs-lookup"><span data-stu-id="5c14c-122">❌ AVOID providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>

 <span data-ttu-id="5c14c-123">Jinými slovy, nemusíte mít vlastnosti, které lze nastavit pomocí konstruktoru i setter.</span><span class="sxs-lookup"><span data-stu-id="5c14c-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="5c14c-124">Tyto zásady jsou velmi jasné, které argumenty jsou volitelné a které jsou povinné, a zabraňují se dvěma způsoby provádění stejných věcí.</span><span class="sxs-lookup"><span data-stu-id="5c14c-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>

 <span data-ttu-id="5c14c-125">❌ Vyhněte se přetížení konstruktorů vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="5c14c-125">❌ AVOID overloading custom attribute constructors.</span></span>

 <span data-ttu-id="5c14c-126">Existence pouze jednoho konstruktoru jasně komunikuje s uživatelem, který argumenty jsou povinné a které jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="5c14c-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>

 <span data-ttu-id="5c14c-127">Pokud je to možné, ✔️ zapečetit vlastní třídy atributů.</span><span class="sxs-lookup"><span data-stu-id="5c14c-127">✔️ DO seal custom attribute classes, if possible.</span></span> <span data-ttu-id="5c14c-128">Díky tomu je hledání atributu rychlejší.</span><span class="sxs-lookup"><span data-stu-id="5c14c-128">This makes the look-up for the attribute faster.</span></span>

 <span data-ttu-id="5c14c-129">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="5c14c-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5c14c-130">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="5c14c-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5c14c-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c14c-131">See also</span></span>

- [<span data-ttu-id="5c14c-132">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="5c14c-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="5c14c-133">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="5c14c-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
