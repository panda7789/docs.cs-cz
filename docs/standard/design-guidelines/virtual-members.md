---
title: Virtuální členové
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
caps.latest.revision: 9
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1b7abe1dbeb7f4888dd8ee4001b410cc583935c4
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="virtual-members"></a><span data-ttu-id="60e3d-102">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="60e3d-102">Virtual Members</span></span>
<span data-ttu-id="60e3d-103">Virtuální členové lze přepsat, čímž dojde ke změně chování podtřídy.</span><span class="sxs-lookup"><span data-stu-id="60e3d-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="60e3d-104">Jsou velmi podobné zpětná volání z hlediska rozšiřitelnosti, které poskytují, ale jsou lepší z hlediska provádění výkonu a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="60e3d-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="60e3d-105">Virtuální členové zaregistrované navíc přirozenější ve scénářích, které vyžadují speciální vytváření druh existující typ (specializace).</span><span class="sxs-lookup"><span data-stu-id="60e3d-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="60e3d-106">Virtuální členové vyšší výkon než zpětná volání a události, ale neprovádět lépe než nevirtuálních metody.</span><span class="sxs-lookup"><span data-stu-id="60e3d-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="60e3d-107">Hlavní nevýhodou virtuální členové je, že chování člena virtuální může upravit pouze v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="60e3d-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="60e3d-108">Chování zpětné volání lze upravit za běhu.</span><span class="sxs-lookup"><span data-stu-id="60e3d-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="60e3d-109">Virtuální členové, jako je zpětných volání (a může být více než zpětná volání), jsou nákladná pro návrh, testování a udržovat, protože všechny volání člena virtuální mohou být přepsána nastaveními v nepředvídatelnými způsoby a mohou spustit libovolný kód.</span><span class="sxs-lookup"><span data-stu-id="60e3d-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="60e3d-110">Kromě toho mnohem víc úsilí většinou vyžaduje jasně definovat kontrakt virtuální členové tak, aby vyšší náklady na návrh a dokumentaci jejich.</span><span class="sxs-lookup"><span data-stu-id="60e3d-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="60e3d-111">**X nesmí** zkontrolujte virtuální členy, pokud máte dobrý důvod k tomu a jste si vědomi veškeré náklady související s návrh, testování a údržbě virtuální členy.</span><span class="sxs-lookup"><span data-stu-id="60e3d-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="60e3d-112">Virtuální členové jsou menší dovolí z hlediska změn, které můžete provedeny k nim, aniž by vás kompatibility.</span><span class="sxs-lookup"><span data-stu-id="60e3d-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="60e3d-113">Navíc jsou nižší než nevirtuálních členy nejčastěji, protože nejsou vloženou obslužnou volání virtuální členové.</span><span class="sxs-lookup"><span data-stu-id="60e3d-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="60e3d-114">**✓ ZVAŽTE** omezení rozšiřitelnost pouze co je to nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="60e3d-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="60e3d-115">**PROVEĎTE ✓** raději chráněné usnadnění přes veřejnou dostupnost pro virtuální členy.</span><span class="sxs-lookup"><span data-stu-id="60e3d-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="60e3d-116">Veřejné členy by měl poskytovat rozšiřitelnost (v případě potřeby) pomocí volání do chráněného člena virtuální.</span><span class="sxs-lookup"><span data-stu-id="60e3d-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="60e3d-117">Veřejné členy třídy by měl poskytovat správnou sadu funkcí pro přímé příjemce této třídy.</span><span class="sxs-lookup"><span data-stu-id="60e3d-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="60e3d-118">Virtuální členové jsou určeny k přepsání v podtřídách a chráněné usnadnění je skvělý způsob, jak obor všechny body rozšiřitelnosti virtuální kterém můžou použít.</span><span class="sxs-lookup"><span data-stu-id="60e3d-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="60e3d-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="60e3d-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="60e3d-120">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="60e3d-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e3d-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="60e3d-121">See Also</span></span>  
 [<span data-ttu-id="60e3d-122">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="60e3d-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="60e3d-123">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="60e3d-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
