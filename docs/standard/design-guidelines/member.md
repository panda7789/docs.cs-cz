---
title: Pokyny k návrhu člena
description: Přečtěte si pokyny pro návrh členů v .NET. Členy zahrnují metody, vlastnosti, události, konstruktory a pole.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: a1f0c1d74e8bffa7cfef975c7dafb9fd01479470
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594488"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="76fee-104">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="76fee-104">Member Design Guidelines</span></span>
<span data-ttu-id="76fee-105">Metody, vlastnosti, události, konstruktory a pole jsou souhrnně označovány jako členy.</span><span class="sxs-lookup"><span data-stu-id="76fee-105">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="76fee-106">Členy jsou nakonec prostředky, pomocí kterých jsou funkce architektury vystavena koncovým uživatelům rozhraní.</span><span class="sxs-lookup"><span data-stu-id="76fee-106">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="76fee-107">Členy můžou být virtuální nebo nevirtuální, konkrétní nebo abstraktní, statické nebo instance a můžou mít několik různých oborů dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="76fee-107">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="76fee-108">Všechna tato odrůdová rozhraní poskytují neexpresivityelné, ale ve stejnou dobu vyžadují péči o součást návrháře architektury.</span><span class="sxs-lookup"><span data-stu-id="76fee-108">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="76fee-109">Tato kapitola nabízí základní pokyny, které by měly být dodrženy při navrhování členů libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="76fee-109">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76fee-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="76fee-110">In This Section</span></span>  
 [<span data-ttu-id="76fee-111">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="76fee-111">Member Overloading</span></span>](member-overloading.md)  
 [<span data-ttu-id="76fee-112">Návrh vlastnosti</span><span class="sxs-lookup"><span data-stu-id="76fee-112">Property Design</span></span>](property.md)  
 [<span data-ttu-id="76fee-113">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="76fee-113">Constructor Design</span></span>](constructor.md)  
 [<span data-ttu-id="76fee-114">Návrh události</span><span class="sxs-lookup"><span data-stu-id="76fee-114">Event Design</span></span>](event.md)  
 [<span data-ttu-id="76fee-115">Návrh pole</span><span class="sxs-lookup"><span data-stu-id="76fee-115">Field Design</span></span>](field.md)  
 [<span data-ttu-id="76fee-116">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="76fee-116">Extension Methods</span></span>](extension-methods.md)  
 [<span data-ttu-id="76fee-117">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="76fee-117">Operator Overloads</span></span>](operator-overloads.md)  
 [<span data-ttu-id="76fee-118">Návrh parametru</span><span class="sxs-lookup"><span data-stu-id="76fee-118">Parameter Design</span></span>](parameter-design.md)  
 <span data-ttu-id="76fee-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="76fee-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="76fee-120">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="76fee-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76fee-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="76fee-121">See also</span></span>

- [<span data-ttu-id="76fee-122">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="76fee-122">Framework Design Guidelines</span></span>](index.md)
