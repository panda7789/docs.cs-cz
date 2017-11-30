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
ms.openlocfilehash: d7b680c3377cbfa40734a57f9408d9487dbf3769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="abstract-class-design"></a><span data-ttu-id="66046-102">Abstraktní třída návrhu</span><span class="sxs-lookup"><span data-stu-id="66046-102">Abstract Class Design</span></span>
<span data-ttu-id="66046-103">**X nesmí** definice veřejných nebo chráněného interní konstruktorů v abstraktních typech.</span><span class="sxs-lookup"><span data-stu-id="66046-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="66046-104">Konstruktory by měly být veřejné pouze v případě, že uživatelé budou potřebovat pro vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="66046-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="66046-105">Protože nelze vytvořit instanci abstraktního typu, s veřejný konstruktor abstraktní typ je nesprávně navrženou a zavádějící uživatelům.</span><span class="sxs-lookup"><span data-stu-id="66046-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="66046-106">**PROVEĎTE ✓** definice s chráněným nebo interní konstruktor v abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="66046-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="66046-107">Chráněný konstruktor je dnes běžné a jednoduše umožňuje udělat vlastní inicializaci, když se vytvoří podtypů základní třídy.</span><span class="sxs-lookup"><span data-stu-id="66046-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="66046-108">Interní konstruktor lze použít k omezení konkrétní implementace abstraktní třídu pro sestavení definice třídy.</span><span class="sxs-lookup"><span data-stu-id="66046-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="66046-109">**PROVEĎTE ✓** zadejte alespoň jeden konkrétní typ, který dědí z každé abstraktní třída, která můžete dodávat.</span><span class="sxs-lookup"><span data-stu-id="66046-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="66046-110">Díky této pomáhá ověření návrhu abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="66046-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="66046-111">Například <xref:System.IO.FileStream?displayProperty=nameWithType> je implementací <xref:System.IO.Stream?displayProperty=nameWithType> abstraktní třídy.</span><span class="sxs-lookup"><span data-stu-id="66046-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="66046-112">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="66046-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="66046-113">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="66046-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66046-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="66046-114">See Also</span></span>  
 [<span data-ttu-id="66046-115">Typ pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="66046-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="66046-116">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="66046-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
