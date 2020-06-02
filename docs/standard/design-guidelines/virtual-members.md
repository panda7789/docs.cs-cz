---
title: Virtuální členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 9eb6cbef969e51dee1a72d402c124d06f08fe5c4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288495"
---
# <a name="virtual-members"></a><span data-ttu-id="8eb1e-102">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="8eb1e-102">Virtual Members</span></span>
<span data-ttu-id="8eb1e-103">Virtuální členy lze přepsat, čímž se mění chování podtřídy.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="8eb1e-104">Jsou poměrně podobné zpětným voláním z důvodu rozšiřitelnosti, kterou poskytují, ale jsou lepší v souvislosti s výkonem spuštění a spotřebou paměti.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="8eb1e-105">Virtuální členové také ve scénářích, které vyžadují vytvoření speciálního druhu stávajícího typu (specializace), mají větší přirozený charakter.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="8eb1e-106">Virtuální členové provádějí lepší než zpětná volání a události, ale neprovádějí lepší než virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="8eb1e-107">Hlavní nevýhodou virtuálních členů je, že chování virtuálního člena lze upravit pouze v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="8eb1e-108">Chování zpětného volání lze upravit v době běhu.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-108">The behavior of a callback can be modified at run time.</span></span>

 <span data-ttu-id="8eb1e-109">Virtuální členové, například zpětná volání (a možná více než zpětná volání), jsou nákladné pro návrh, testování a údržbu, protože jakékoli volání virtuálního člena lze přepsat nepředvídatelným způsobem a může spustit libovolný kód.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="8eb1e-110">K jasnému definování kontraktů virtuálních členů se obvykle vyžaduje mnohem více úsilí, takže náklady na jejich navrhování a dokumentaci jsou vyšší.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="8eb1e-111">❌Nevytvářejte členy Virtual, pokud nemáte dobrý důvod k tomu, abyste se dozvěděli o všech nákladech souvisejících s návrhem, testováním a údržbou virtuálních členů.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="8eb1e-112">Virtuální členové jsou méně striktní z hlediska změn, které je možné v nich provést bez narušení kompatibility.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="8eb1e-113">Jsou také pomalejší než nevirtuální členové, většinou protože volání virtuálních členů nejsou vložena.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="8eb1e-114">✔️ Zvažte omezení rozšiřitelnosti jenom na to, co je nezbytně nutné.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="8eb1e-115">✔️ preferovat chráněnou přístupnost prostřednictvím veřejné dostupnosti pro virtuální členy.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="8eb1e-116">Veřejné členy by měli poskytnout rozšíření (v případě potřeby) voláním do chráněného virtuálního člena.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="8eb1e-117">Veřejné členy třídy by měli poskytnout správnou sadu funkcí pro přímé spotřebitele této třídy.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="8eb1e-118">Virtuální členové jsou navrženi pro přepsání v podtříd a chráněná přístupnost je skvělým způsobem pro vymezení všech virtuálních bodů rozšiřitelnosti na místo, kde je lze použít.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="8eb1e-119">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="8eb1e-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8eb1e-120">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="8eb1e-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8eb1e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="8eb1e-121">See also</span></span>

- [<span data-ttu-id="8eb1e-122">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="8eb1e-122">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="8eb1e-123">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="8eb1e-123">Designing for Extensibility</span></span>](designing-for-extensibility.md)
