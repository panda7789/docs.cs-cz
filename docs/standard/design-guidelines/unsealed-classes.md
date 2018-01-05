---
title: "Nezapečetěné třídy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ec66fb3dea74e6f738ec308ce0f88945526a0a77
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="unsealed-classes"></a><span data-ttu-id="750f0-102">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="750f0-102">Unsealed Classes</span></span>
<span data-ttu-id="750f0-103">Zapečetěné třídy nelze zděděno z a zabraňují rozšíření.</span><span class="sxs-lookup"><span data-stu-id="750f0-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="750f0-104">Třídy, které je možné zdědit z se nazývají naproti nezapečetěných třídy.</span><span class="sxs-lookup"><span data-stu-id="750f0-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="750f0-105">**✓ ZVAŽTE** použití nezapečetěných tříd bez přidat virtuální nebo chráněné členy, protože skvělý způsob, jak poskytnout nenákladné ještě mnohem vezme v úvahu rozšíření na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="750f0-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="750f0-106">Vývojáři se často chtějí dědění z tříd nezapečetěných která přidat členy pohodlí například vlastní konstruktory, nové metody nebo přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="750f0-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="750f0-107">Například `System.Messaging.MessageQueue` nezapečetěná, a proto umožňuje uživatelům vytvářet vlastní fronty této výchozí do konkrétní fronty cesty, nebo při přidání vlastních metod, které zjednodušují rozhraní API pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="750f0-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="750f0-108">Třídy jsou nezapečetěné ve výchozím nastavení většina programovacích jazyků, který je taky doporučené výchozí nastavení pro Většina tříd v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="750f0-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="750f0-109">Rozšiřitelnost poskytované nezapečetěných typy je mnohem vezme v úvahu uživatelé framework a poměrně málo zajistit kvůli relativně nízký testovací náklady spojené s nezapečetěné typy.</span><span class="sxs-lookup"><span data-stu-id="750f0-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="750f0-110">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="750f0-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="750f0-111">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="750f0-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="750f0-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="750f0-112">See Also</span></span>  
 [<span data-ttu-id="750f0-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="750f0-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="750f0-114">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="750f0-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)  
 [<span data-ttu-id="750f0-115">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="750f0-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
