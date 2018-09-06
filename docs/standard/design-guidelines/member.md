---
title: Pokyny k návrhu člena
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1598ac63af38f1ca3e11104bc8e1cd6323d35ed
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871015"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="27fcd-102">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="27fcd-102">Member Design Guidelines</span></span>
<span data-ttu-id="27fcd-103">Metody, vlastnosti, události, konstruktory a pole se souhrnně označují jako členy.</span><span class="sxs-lookup"><span data-stu-id="27fcd-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="27fcd-104">Členové jsou takže v konečném důsledku znamená, podle kterého je funkce rozhraní zpřístupněny koncovým uživatelům o architektuře.</span><span class="sxs-lookup"><span data-stu-id="27fcd-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="27fcd-105">Členové může být statická virtuální a nevirtuální, konkrétní nebo abstraktní, nebo instance a může mít několik různých oborech přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="27fcd-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="27fcd-106">Tento různých poskytuje neuvěřitelné expresivity, ale ve stejnou dobu vyžaduje péči ze strany framework designer.</span><span class="sxs-lookup"><span data-stu-id="27fcd-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="27fcd-107">Tato kapitola nabízí základní pokyny, které byste měli dodržet, při navrhování členy libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="27fcd-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="27fcd-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="27fcd-108">In This Section</span></span>  
 [<span data-ttu-id="27fcd-109">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="27fcd-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="27fcd-110">Návrh vlastnosti</span><span class="sxs-lookup"><span data-stu-id="27fcd-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="27fcd-111">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="27fcd-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="27fcd-112">Návrh události</span><span class="sxs-lookup"><span data-stu-id="27fcd-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="27fcd-113">Návrh pole</span><span class="sxs-lookup"><span data-stu-id="27fcd-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="27fcd-114">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="27fcd-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="27fcd-115">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="27fcd-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="27fcd-116">Návrh parametru</span><span class="sxs-lookup"><span data-stu-id="27fcd-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="27fcd-117">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="27fcd-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="27fcd-118">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="27fcd-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fcd-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27fcd-119">See also</span></span>

- [<span data-ttu-id="27fcd-120">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="27fcd-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
