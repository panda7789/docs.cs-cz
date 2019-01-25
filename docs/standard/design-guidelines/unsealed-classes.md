---
title: Nezapečetěné třídy
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616927"
---
# <a name="unsealed-classes"></a><span data-ttu-id="06396-102">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="06396-102">Unsealed Classes</span></span>
<span data-ttu-id="06396-103">Zapečetěné třídy nelze dědit z, a brání tomu, aby rozšíření.</span><span class="sxs-lookup"><span data-stu-id="06396-103">Sealed classes cannot be inherited from, and they prevent extensibility.</span></span> <span data-ttu-id="06396-104">Třídy, které je možné zdědit z naproti tomu se nazývají nezapečetěné třídy.</span><span class="sxs-lookup"><span data-stu-id="06396-104">In contrast, classes that can be inherited from are called unsealed classes.</span></span>  
  
 <span data-ttu-id="06396-105">**✓ CONSIDER** použití nezapečetěných tříd bez přidat virtuální nebo chráněné členy, protože skvělý způsob, jak poskytnout nenákladné ještě mnohem vezme v úvahu rozšíření na rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06396-105">**✓ CONSIDER** using unsealed classes with no added virtual or protected members as a great way to provide inexpensive yet much appreciated extensibility to a framework.</span></span>  
  
 <span data-ttu-id="06396-106">Vývojáři často má Zdědit z nezapečetěné třídy tak, aby přidat pohodlí členy jako jsou vlastní konstruktory, nové metody nebo přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="06396-106">Developers often want to inherit from unsealed classes so as to add convenience members such as custom constructors, new methods, or method overloads.</span></span> <span data-ttu-id="06396-107">Například `System.Messaging.MessageQueue` nezapečetěná, a proto umožňuje uživatelům vytvářet vlastní fronty tuto výchozí hodnotu, do konkrétní fronty cesty nebo přidávání vlastních metod, které zjednodušují rozhraní API pro konkrétní scénáře.</span><span class="sxs-lookup"><span data-stu-id="06396-107">For example,  `System.Messaging.MessageQueue` is unsealed and thus allows users to create custom queues that default to a particular queue path or to add custom methods that simplify the API for specific scenarios.</span></span>  
  
 <span data-ttu-id="06396-108">Ve výchozím nastavení ve většině programovacích jazycích jsou nezapečetěné třídy a je také doporučené výchozí nastavení pro většinu tříd v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="06396-108">Classes are unsealed by default in most programming languages, and this is also the recommended default for most classes in frameworks.</span></span> <span data-ttu-id="06396-109">Rozšiřitelnost poskytované nezapečetěné typy je ceníme uživatelé rozhraní framework a poměrně levné poskytnout kvůli relativně nízký testovací náklady spojené s nezapečetěné typy.</span><span class="sxs-lookup"><span data-stu-id="06396-109">The extensibility afforded by unsealed types is much appreciated by framework users and quite inexpensive to provide because of relatively low test costs associated with unsealed types.</span></span>  
  
 <span data-ttu-id="06396-110">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="06396-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="06396-111">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="06396-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06396-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06396-112">See also</span></span>

- [<span data-ttu-id="06396-113">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="06396-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="06396-114">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="06396-114">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [<span data-ttu-id="06396-115">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="06396-115">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)
