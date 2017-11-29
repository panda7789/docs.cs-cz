---
title: Attributes1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86fa2556e6b8fb82e31a7d4753354aa2dff627ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="attributes"></a><span data-ttu-id="1d59e-102">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d59e-102">Attributes</span></span>
<span data-ttu-id="1d59e-103"><xref:System.Attribute?displayProperty=nameWithType>je základní třídu používá k definování vlastní atributy.</span><span class="sxs-lookup"><span data-stu-id="1d59e-103"><xref:System.Attribute?displayProperty=nameWithType> is a base class used to define custom attributes.</span></span>  
  
 <span data-ttu-id="1d59e-104">Poznámky přidané k elementům programování například sestavení, typy, členů a parametry jsou atributy.</span><span class="sxs-lookup"><span data-stu-id="1d59e-104">Attributes are annotations that can be added to programming elements such as assemblies, types, members, and parameters.</span></span> <span data-ttu-id="1d59e-105">Tyto jsou uložené v metadatech sestavení a je přístupný v době běhu pomocí rozhraní API reflexe.</span><span class="sxs-lookup"><span data-stu-id="1d59e-105">They are stored in the metadata of the assembly and can be accessed at runtime using the reflection APIs.</span></span> <span data-ttu-id="1d59e-106">Například rozhraní definuje <xref:System.ObsoleteAttribute>, který je možné použít pro určitý typ nebo člen k označení, že typ nebo člen je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="1d59e-106">For example, the Framework defines the <xref:System.ObsoleteAttribute>, which can be applied to a type or a member to indicate that the type or member has been deprecated.</span></span>  
  
 <span data-ttu-id="1d59e-107">Atributy mohou mít jednu nebo více vlastností, které zajišťují další data související s atribut.</span><span class="sxs-lookup"><span data-stu-id="1d59e-107">Attributes can have one or more properties that carry additional data related to the attribute.</span></span> <span data-ttu-id="1d59e-108">Například `ObsoleteAttribute` může nést další informace o verzi v která získali nepoužívá typ nebo člen a popis nové rozhraní API nahrazení zastaralá rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1d59e-108">For example, `ObsoleteAttribute` could carry additional information about the release in which a type or a member got deprecated and the description of the new APIs replacing the obsolete API.</span></span>  
  
 <span data-ttu-id="1d59e-109">Některé vlastnosti atributu je třeba zadat při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="1d59e-109">Some properties of an attribute must be specified when the attribute is applied.</span></span> <span data-ttu-id="1d59e-110">Tyto jsou označovány jako požadované vlastnosti nebo povinnými argumenty, protože jsou reprezentovány jako konstruktor poziční parametry.</span><span class="sxs-lookup"><span data-stu-id="1d59e-110">These are referred to as the required properties or required arguments, because they are represented as positional constructor parameters.</span></span> <span data-ttu-id="1d59e-111">Například <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> vlastnost <xref:System.Diagnostics.ConditionalAttribute> je požadovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d59e-111">For example, the <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> property of the <xref:System.Diagnostics.ConditionalAttribute> is a required property.</span></span>  
  
 <span data-ttu-id="1d59e-112">Vlastnosti, které není potřeba zadat, kdy je použit atribut se nazývají volitelných vlastností (nebo volitelné argumenty).</span><span class="sxs-lookup"><span data-stu-id="1d59e-112">Properties that do not necessarily have to be specified when the attribute is applied are called optional properties (or optional arguments).</span></span> <span data-ttu-id="1d59e-113">Jsou zobrazeny v nastavit vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1d59e-113">They are represented by settable properties.</span></span> <span data-ttu-id="1d59e-114">Kompilátory poskytují speciální syntaxe a nastavte tyto vlastnosti, když se použije atribut.</span><span class="sxs-lookup"><span data-stu-id="1d59e-114">Compilers provide special syntax to set these properties when an attribute is applied.</span></span> <span data-ttu-id="1d59e-115">Například <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> vlastnost představuje za volitelným argumentem.</span><span class="sxs-lookup"><span data-stu-id="1d59e-115">For example, the <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property represents an optional argument.</span></span>  
  
 <span data-ttu-id="1d59e-116">**PROVEĎTE ✓** název třídy vlastních atributů s příponou "Atribut."</span><span class="sxs-lookup"><span data-stu-id="1d59e-116">**✓ DO** name custom attribute classes with the suffix "Attribute."</span></span>  
  
 <span data-ttu-id="1d59e-117">**PROVEĎTE ✓** použít <xref:System.AttributeUsageAttribute> vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="1d59e-117">**✓ DO** apply the <xref:System.AttributeUsageAttribute> to custom attributes.</span></span>  
  
 <span data-ttu-id="1d59e-118">**PROVEĎTE ✓** zadejte nastavit vlastnosti pro volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="1d59e-118">**✓ DO** provide settable properties for optional arguments.</span></span>  
  
 <span data-ttu-id="1d59e-119">**PROVEĎTE ✓** zadejte vlastnosti jen get pro povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="1d59e-119">**✓ DO** provide get-only properties for required arguments.</span></span>  
  
 <span data-ttu-id="1d59e-120">**PROVEĎTE ✓** zadat parametry konstruktor k chybě při inicializaci vlastnosti odpovídající povinnými argumenty.</span><span class="sxs-lookup"><span data-stu-id="1d59e-120">**✓ DO** provide constructor parameters to initialize properties corresponding to required arguments.</span></span> <span data-ttu-id="1d59e-121">Každý parametr by měl mít stejný název (i když se jiný velká a malá písmena) jako odpovídající vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1d59e-121">Each parameter should have the same name (although with different casing) as the corresponding property.</span></span>  
  
 <span data-ttu-id="1d59e-122">**X nepoužívejte** poskytuje konstruktor parametry k chybě při inicializaci vlastnosti odpovídající volitelné argumenty.</span><span class="sxs-lookup"><span data-stu-id="1d59e-122">**X AVOID** providing constructor parameters to initialize properties corresponding to the optional arguments.</span></span>  
  
 <span data-ttu-id="1d59e-123">Jinými slovy nemají vlastnosti, které lze nastavit pomocí konstruktoru a setter.</span><span class="sxs-lookup"><span data-stu-id="1d59e-123">In other words, do not have properties that can be set with both a constructor and a setter.</span></span> <span data-ttu-id="1d59e-124">Toto platí umožňuje velmi explicitní argumenty, které jsou volitelné a které jsou požadovány a tomu není nutné dva způsoby, jak to samé.</span><span class="sxs-lookup"><span data-stu-id="1d59e-124">This guideline makes very explicit which arguments are optional and which are required, and avoids having two ways of doing the same thing.</span></span>  
  
 <span data-ttu-id="1d59e-125">**X nepoužívejte** přetížení konstruktory vlastních atributů.</span><span class="sxs-lookup"><span data-stu-id="1d59e-125">**X AVOID** overloading custom attribute constructors.</span></span>  
  
 <span data-ttu-id="1d59e-126">Má jenom jeden konstruktor jasně komunikuje uživateli, které argumenty jsou povinné a jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="1d59e-126">Having only one constructor clearly communicates to the user which arguments are required and which are optional.</span></span>  
  
 <span data-ttu-id="1d59e-127">**PROVEĎTE ✓** zapečetit vlastní atribut třídy, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="1d59e-127">**✓ DO** seal custom attribute classes, if possible.</span></span> <span data-ttu-id="1d59e-128">Díky tomu rychlejší hledání pro atribut.</span><span class="sxs-lookup"><span data-stu-id="1d59e-128">This makes the look-up for the attribute faster.</span></span>  
  
 <span data-ttu-id="1d59e-129">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="1d59e-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1d59e-130">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1d59e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d59e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d59e-131">See Also</span></span>  
 [<span data-ttu-id="1d59e-132">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="1d59e-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="1d59e-133">Pokyny týkající se používání</span><span class="sxs-lookup"><span data-stu-id="1d59e-133">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
