---
title: "Abstraktní třída návrhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 739f86acd534549bc997dc7a939cf43a0c6fc3cb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="e048c-102">Abstraktní třída návrhu</span><span class="sxs-lookup"><span data-stu-id="e048c-102">Abstract Class Design</span></span>
<span data-ttu-id="e048c-103">**X nesmí** definice veřejných nebo chráněného interní konstruktorů v abstraktních typech.</span><span class="sxs-lookup"><span data-stu-id="e048c-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="e048c-104">Konstruktory by měly být veřejné pouze v případě, že uživatelé budou potřebovat pro vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="e048c-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="e048c-105">Protože nelze vytvořit instanci abstraktního typu, s veřejný konstruktor abstraktní typ je nesprávně navrženou a zavádějící uživatelům.</span><span class="sxs-lookup"><span data-stu-id="e048c-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="e048c-106">**PROVEĎTE ✓** definice s chráněným nebo interní konstruktor v abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="e048c-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="e048c-107">Chráněný konstruktor je dnes běžné a jednoduše umožňuje udělat vlastní inicializaci, když se vytvoří podtypů základní třídy.</span><span class="sxs-lookup"><span data-stu-id="e048c-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="e048c-108">Interní konstruktor lze použít k omezení konkrétní implementace abstraktní třídu pro sestavení definice třídy.</span><span class="sxs-lookup"><span data-stu-id="e048c-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="e048c-109">**PROVEĎTE ✓** zadejte alespoň jeden konkrétní typ, který dědí z každé abstraktní třída, která můžete dodávat.</span><span class="sxs-lookup"><span data-stu-id="e048c-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="e048c-110">Díky této pomáhá ověření návrhu abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="e048c-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="e048c-111">Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementací <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="e048c-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="e048c-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="e048c-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e048c-113">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="e048c-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e048c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e048c-114">See Also</span></span>  
 [<span data-ttu-id="e048c-115">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="e048c-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="e048c-116">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="e048c-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
