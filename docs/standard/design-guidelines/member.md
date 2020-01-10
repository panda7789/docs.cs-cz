---
title: Pokyny k návrhu člena
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: cf4f1d2fee73e3e65dc4d92ea97a62f4a7e4c4e5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709267"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="939f6-102">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="939f6-102">Member Design Guidelines</span></span>
<span data-ttu-id="939f6-103">Metody, vlastnosti, události, konstruktory a pole jsou souhrnně označovány jako členy.</span><span class="sxs-lookup"><span data-stu-id="939f6-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="939f6-104">Členy jsou nakonec prostředky, pomocí kterých jsou funkce architektury vystavena koncovým uživatelům rozhraní.</span><span class="sxs-lookup"><span data-stu-id="939f6-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="939f6-105">Členy můžou být virtuální nebo nevirtuální, konkrétní nebo abstraktní, statické nebo instance a můžou mít několik různých oborů dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="939f6-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="939f6-106">Všechna tato odrůdová rozhraní poskytují neexpresivityelné, ale ve stejnou dobu vyžadují péči o součást návrháře architektury.</span><span class="sxs-lookup"><span data-stu-id="939f6-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="939f6-107">Tato kapitola nabízí základní pokyny, které by měly být dodrženy při navrhování členů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="939f6-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="939f6-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="939f6-108">In This Section</span></span>  
 [<span data-ttu-id="939f6-109">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="939f6-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="939f6-110">Návrh vlastnosti</span><span class="sxs-lookup"><span data-stu-id="939f6-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="939f6-111">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="939f6-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="939f6-112">Návrh události</span><span class="sxs-lookup"><span data-stu-id="939f6-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="939f6-113">Návrh pole</span><span class="sxs-lookup"><span data-stu-id="939f6-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="939f6-114">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="939f6-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="939f6-115">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="939f6-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="939f6-116">Návrh parametru</span><span class="sxs-lookup"><span data-stu-id="939f6-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="939f6-117">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="939f6-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="939f6-118">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="939f6-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="939f6-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="939f6-119">See also</span></span>

- [<span data-ttu-id="939f6-120">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="939f6-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
