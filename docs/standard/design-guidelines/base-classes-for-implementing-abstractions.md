---
title: "Základní třídy pro implementaci abstrakce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- abstractions [.NET Framework]
- base classes, abstractions
ms.assetid: 37a2d9a4-9721-482a-a40f-eee2c1d97875
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 96264456ac6afc569c46caf5faed6c37ea22bc8e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="base-classes-for-implementing-abstractions"></a><span data-ttu-id="a2898-102">Základní třídy pro implementaci abstrakce</span><span class="sxs-lookup"><span data-stu-id="a2898-102">Base Classes for Implementing Abstractions</span></span>
<span data-ttu-id="a2898-103">Přesněji řečeno třídu změní základní třídy, pokud je z něj odvozenou jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="a2898-103">Strictly speaking, a class becomes a base class when another class is derived from it.</span></span> <span data-ttu-id="a2898-104">Pro účely této části je však základní třídu třídu určena především k poskytování běžné abstrakce nebo pro jiné třídy znovu použít některé výchozí implementace ale dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="a2898-104">For the purpose of this section, however, a base class is a class designed mainly to provide a common abstraction or for other classes to reuse some default implementation though inheritance.</span></span> <span data-ttu-id="a2898-105">Základní třídy se obvykle nacházejí uprostřed hierarchie dědičnosti mezi několik vlastní implementace v dolní části a abstrakci na nejnižší úrovni hierarchie.</span><span class="sxs-lookup"><span data-stu-id="a2898-105">Base classes usually sit in the middle of inheritance hierarchies, between an abstraction at the root of a hierarchy and several custom implementations at the bottom.</span></span>  
  
 <span data-ttu-id="a2898-106">Pro implementaci abstrakce představují implementace pomocné rutiny.</span><span class="sxs-lookup"><span data-stu-id="a2898-106">They serve as implementation helpers for implementing abstractions.</span></span> <span data-ttu-id="a2898-107">Je například jeden z rozhraní Framework abstrakci pro seřazené kolekce položek <xref:System.Collections.Generic.IList%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a2898-107">For example, one of the Framework’s abstractions for ordered collections of items is the <xref:System.Collections.Generic.IList%601> interface.</span></span> <span data-ttu-id="a2898-108">Implementace <xref:System.Collections.Generic.IList%601> není triviální, a proto rozhraní Framework poskytuje několik základní třídy, jako například <xref:System.Collections.ObjectModel.Collection%601> a <xref:System.Collections.ObjectModel.KeyedCollection%602>, který slouží jako pomocné rutiny pro implementaci vlastní kolekce.</span><span class="sxs-lookup"><span data-stu-id="a2898-108">Implementing <xref:System.Collections.Generic.IList%601> is not trivial, and therefore the Framework provides several base classes, such as <xref:System.Collections.ObjectModel.Collection%601> and <xref:System.Collections.ObjectModel.KeyedCollection%602>, which serve as helpers for implementing custom collections.</span></span>  
  
 <span data-ttu-id="a2898-109">Třídy Base obvykle nejsou vhodná, která bude sloužit jako abstrakce sami, protože se zpravidla obsahuje příliš mnoho implementace.</span><span class="sxs-lookup"><span data-stu-id="a2898-109">Base classes are usually not suited to serve as abstractions by themselves, because they tend to contain too much implementation.</span></span> <span data-ttu-id="a2898-110">Například `Collection<T>` základní třída obsahuje spoustu implementace souvisí se skutečností, že implementuje neobecné `IList` rozhraní (aby lépe integrovat neobecné kolekce) a na skutečnost, že je kolekce položek uložená v paměti v jednom z jeho polí.</span><span class="sxs-lookup"><span data-stu-id="a2898-110">For example, the `Collection<T>` base class contains lots of implementation related to the fact that it implements the nongeneric `IList` interface (to integrate better with nongeneric collections) and to the fact that it is a collection of items stored in memory in one of its fields.</span></span>  
  
 <span data-ttu-id="a2898-111">Jak je uvedeno výše, základní třídy pro uživatele, kteří potřebují k implementaci abstrakce poskytnout neocenitelnou pomocí nápovědy, ale současně se může být důležité odpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="a2898-111">As previously discussed, base classes can provide invaluable help for users who need to implement abstractions, but at the same time they can be a significant liability.</span></span> <span data-ttu-id="a2898-112">Jejich přidejte útoku a zvýšit hloubku hierarchie dědičnosti a proto koncepčně zkomplikovat rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a2898-112">They add surface area and increase the depth of inheritance hierarchies and so conceptually complicate the framework.</span></span> <span data-ttu-id="a2898-113">Proto základní třídy by měl používat pouze v případě, že poskytují významné zlepšení uživatelům rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a2898-113">Therefore, base classes should be used only if they provide significant value to the users of the framework.</span></span> <span data-ttu-id="a2898-114">Budou se vyhnout, pokud poskytují hodnotu pouze pro implementátory architekturu, ve kterém případu delegování interní implementace místo dědění ze základní třídy silného považovat.</span><span class="sxs-lookup"><span data-stu-id="a2898-114">They should be avoided if they provide value only to the implementers of the framework, in which case delegation to an internal implementation instead of inheritance from a base class should be strongly considered.</span></span>  
  
 <span data-ttu-id="a2898-115">**✓ ZVAŽTE** provedení základní třídy abstraktní i v případě, že neobsahují žádné abstraktní členy.</span><span class="sxs-lookup"><span data-stu-id="a2898-115">**✓ CONSIDER** making base classes abstract even if they don’t contain any abstract members.</span></span> <span data-ttu-id="a2898-116">To jasně komunikuje uživatelům určený výhradně k možné zdědit z třídy.</span><span class="sxs-lookup"><span data-stu-id="a2898-116">This clearly communicates to the users that the class is designed solely to be inherited from.</span></span>  
  
 <span data-ttu-id="a2898-117">**✓ ZVAŽTE** umístění základních tříd do samostatného oboru názvů z nejdůležitějších scénář typů.</span><span class="sxs-lookup"><span data-stu-id="a2898-117">**✓ CONSIDER** placing base classes in a separate namespace from the mainline scenario types.</span></span> <span data-ttu-id="a2898-118">Podle definice základní třídy jsou určené pro scénáře pokročilé rozšiřitelnost a proto nejsou zajímavé pro většinu uživatelů.</span><span class="sxs-lookup"><span data-stu-id="a2898-118">By definition, base classes are intended for advanced extensibility scenarios and therefore are not interesting to the majority of users.</span></span>  
  
 <span data-ttu-id="a2898-119">**X nepoužívejte** pojmenování základní třídy s příponou "Základní", pokud třída je určena pro použití v veřejná rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a2898-119">**X AVOID** naming base classes with a "Base" suffix if the class is intended for use in public APIs.</span></span>  
  
 <span data-ttu-id="a2898-120">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="a2898-120">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a2898-121">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="a2898-121">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2898-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2898-122">See Also</span></span>  
 [<span data-ttu-id="a2898-123">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="a2898-123">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="a2898-124">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="a2898-124">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
