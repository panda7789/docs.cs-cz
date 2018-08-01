---
title: Člen pokynů pro návrh
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
ms.openlocfilehash: 1c04b431224a1d4f03e85397b854a52856e114e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571394"
---
# <a name="member-design-guidelines"></a><span data-ttu-id="9e5f8-102">Člen pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="9e5f8-102">Member Design Guidelines</span></span>
<span data-ttu-id="9e5f8-103">Metody, vlastnosti, události, konstruktory a pole se souhrnně označují jako členy.</span><span class="sxs-lookup"><span data-stu-id="9e5f8-103">Methods, properties, events, constructors, and fields are collectively referred to as members.</span></span> <span data-ttu-id="9e5f8-104">Členy jsou nakonec prostředky, se kterým je funkce framework zpřístupněny koncovým uživatelům prostředí.</span><span class="sxs-lookup"><span data-stu-id="9e5f8-104">Members are ultimately the means by which framework functionality is exposed to the end users of a framework.</span></span>  
  
 <span data-ttu-id="9e5f8-105">Členové můžou být statické virtuální nebo nevirtuální, konkrétní nebo abstraktní, nebo instance a může mít několik různými obory usnadnění.</span><span class="sxs-lookup"><span data-stu-id="9e5f8-105">Members can be virtual or nonvirtual, concrete or abstract, static or instance, and can have several different scopes of accessibility.</span></span> <span data-ttu-id="9e5f8-106">Všechna tato různých poskytuje neuvěřitelné expressiveness, ale současně vyžaduje pozornost ze strany návrháře framework.</span><span class="sxs-lookup"><span data-stu-id="9e5f8-106">All this variety provides incredible expressiveness but at the same time requires care on the part of the framework designer.</span></span>  
  
 <span data-ttu-id="9e5f8-107">Tato kapitola nabízí základní pokyny, které by se měly dodržovat při navrhování členy libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="9e5f8-107">This chapter offers basic guidelines that should be followed when designing members of any type.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e5f8-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9e5f8-108">In This Section</span></span>  
 [<span data-ttu-id="9e5f8-109">Přetížení člena</span><span class="sxs-lookup"><span data-stu-id="9e5f8-109">Member Overloading</span></span>](../../../docs/standard/design-guidelines/member-overloading.md)  
 [<span data-ttu-id="9e5f8-110">Návrh vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9e5f8-110">Property Design</span></span>](../../../docs/standard/design-guidelines/property.md)  
 [<span data-ttu-id="9e5f8-111">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="9e5f8-111">Constructor Design</span></span>](../../../docs/standard/design-guidelines/constructor.md)  
 [<span data-ttu-id="9e5f8-112">Návrh události</span><span class="sxs-lookup"><span data-stu-id="9e5f8-112">Event Design</span></span>](../../../docs/standard/design-guidelines/event.md)  
 [<span data-ttu-id="9e5f8-113">Návrh pole</span><span class="sxs-lookup"><span data-stu-id="9e5f8-113">Field Design</span></span>](../../../docs/standard/design-guidelines/field.md)  
 [<span data-ttu-id="9e5f8-114">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="9e5f8-114">Extension Methods</span></span>](../../../docs/standard/design-guidelines/extension-methods.md)  
 [<span data-ttu-id="9e5f8-115">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="9e5f8-115">Operator Overloads</span></span>](../../../docs/standard/design-guidelines/operator-overloads.md)  
 [<span data-ttu-id="9e5f8-116">Návrh parametru</span><span class="sxs-lookup"><span data-stu-id="9e5f8-116">Parameter Design</span></span>](../../../docs/standard/design-guidelines/parameter-design.md)  
 <span data-ttu-id="9e5f8-117">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="9e5f8-117">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9e5f8-118">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="9e5f8-118">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5f8-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e5f8-119">See Also</span></span>  
 [<span data-ttu-id="9e5f8-120">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="9e5f8-120">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
