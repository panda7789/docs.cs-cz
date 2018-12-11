---
title: Virtuální členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
author: KrzysztofCwalina
ms.openlocfilehash: 1719e9843252c25d1e799471330c6cb08211245b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128921"
---
# <a name="virtual-members"></a><span data-ttu-id="a3e5b-102">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="a3e5b-102">Virtual Members</span></span>
<span data-ttu-id="a3e5b-103">Virtuální členové lze přepsat, čímž se změní chování podtřídy.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="a3e5b-104">Jsou na zpětná volání z hlediska rozšiřitelnosti, které poskytují velmi podobné, ale jsou lepší z hlediska provádění výkonu a využití paměti.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="a3e5b-105">Navíc můžete virtuální členy přirozenější ve scénářích, které vyžadují vytvoření zvláštní druh existujícího typu (specializace).</span><span class="sxs-lookup"><span data-stu-id="a3e5b-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>  
  
 <span data-ttu-id="a3e5b-106">Virtuální členové poskytují vyšší výkon než zpětná volání a události, ale neprovádět lépe než nevirtuální metody.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>  
  
 <span data-ttu-id="a3e5b-107">Hlavní nevýhodou virtuální členy je, že chování virtuálního člena lze změnit pouze v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="a3e5b-108">Chování zpětné volání, lze upravit za běhu.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-108">The behavior of a callback can be modified at runtime.</span></span>  
  
 <span data-ttu-id="a3e5b-109">Virtuální členy jako zpětná volání (a možná víc než zpětná volání), je nákladné navrhnout, testovat a spravovat, protože jakékoli volání virtuálního členu mohou být přepsána nastaveními v nepředvídatelnými způsoby a může spustit libovolný kód.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="a3e5b-110">Navíc je k jasně definovat kontrakt virtuální členy, tedy vyšší náklady na navrhování a dokumentace je většinou potřeba mnohem větší úsilí.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>  
  
 <span data-ttu-id="a3e5b-111">**X DO NOT** zkontrolujte virtuální členy, pokud máte dobrý důvod k tomu a jste si vědomi veškeré náklady související s návrh, testování a údržbě virtuální členy.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-111">**X DO NOT** make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>  
  
 <span data-ttu-id="a3e5b-112">Virtuální členy jsou méně striktní z hlediska změn, které můžete k nim nevytváří bez porušení kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="a3e5b-113">Navíc jsou pomalejší než nevirtuální členy, většinou, protože volání virtuální členy nejsou vložené.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>  
  
 <span data-ttu-id="a3e5b-114">**✓ CONSIDER** omezení rozšiřitelnost pouze co je to nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-114">**✓ CONSIDER** limiting extensibility to only what is absolutely necessary.</span></span>  
  
 <span data-ttu-id="a3e5b-115">**✓ DO** raději chráněné usnadnění přes veřejnou dostupnost pro virtuální členy.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-115">**✓ DO** prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="a3e5b-116">Veřejné členy by měl zajistí možnosti rozšíření (v případě potřeby) ve volání do chráněná virtuální členská funkce.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>  
  
 <span data-ttu-id="a3e5b-117">Veřejné členy třídy by měly poskytnout správné sady funkcí pro přímé zákazníky této třídy.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="a3e5b-118">Virtuální členy jsou určeny k přepsání v podtřídách a chráněné přístupnost je skvělý způsob, jak oboru, ve kterém můžou použít všechny body rozšiřitelnosti virtuální.</span><span class="sxs-lookup"><span data-stu-id="a3e5b-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>  
  
 <span data-ttu-id="a3e5b-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="a3e5b-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a3e5b-120">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="a3e5b-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e5b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3e5b-121">See also</span></span>

- [<span data-ttu-id="a3e5b-122">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="a3e5b-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="a3e5b-123">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="a3e5b-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
