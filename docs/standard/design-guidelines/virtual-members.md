---
title: Virtuální členové
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- overridable members
- virtual members
- members [.NET Framework], virtual
ms.assetid: 8ff4eb97-0364-43ec-8a02-934b5cd94d19
ms.openlocfilehash: 8ed519a01162056151d8ae6398c0d06495911afd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743525"
---
# <a name="virtual-members"></a><span data-ttu-id="646f9-102">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="646f9-102">Virtual Members</span></span>
<span data-ttu-id="646f9-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span><span class="sxs-lookup"><span data-stu-id="646f9-103">Virtual members can be overridden, thus changing the behavior of the subclass.</span></span> <span data-ttu-id="646f9-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span><span class="sxs-lookup"><span data-stu-id="646f9-104">They are quite similar to callbacks in terms of the extensibility they provide, but they are better in terms of execution performance and memory consumption.</span></span> <span data-ttu-id="646f9-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span><span class="sxs-lookup"><span data-stu-id="646f9-105">Also, virtual members feel more natural in scenarios that require creating a special kind of an existing type (specialization).</span></span>

 <span data-ttu-id="646f9-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span><span class="sxs-lookup"><span data-stu-id="646f9-106">Virtual members perform better than callbacks and events, but do not perform better than non-virtual methods.</span></span>

 <span data-ttu-id="646f9-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span><span class="sxs-lookup"><span data-stu-id="646f9-107">The main disadvantage of virtual members is that the behavior of a virtual member can only be modified at the time of compilation.</span></span> <span data-ttu-id="646f9-108">The behavior of a callback can be modified at runtime.</span><span class="sxs-lookup"><span data-stu-id="646f9-108">The behavior of a callback can be modified at runtime.</span></span>

 <span data-ttu-id="646f9-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span><span class="sxs-lookup"><span data-stu-id="646f9-109">Virtual members, like callbacks (and maybe more than callbacks), are costly to design, test, and maintain because any call to a virtual member can be overridden in unpredictable ways and can execute arbitrary code.</span></span> <span data-ttu-id="646f9-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span><span class="sxs-lookup"><span data-stu-id="646f9-110">Also, much more effort is usually required to clearly define the contract of virtual members, so the cost of designing and documenting them is higher.</span></span>

 <span data-ttu-id="646f9-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span><span class="sxs-lookup"><span data-stu-id="646f9-111">❌ DO NOT make members virtual unless you have a good reason to do so and you are aware of all the costs related to designing, testing, and maintaining virtual members.</span></span>

 <span data-ttu-id="646f9-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span><span class="sxs-lookup"><span data-stu-id="646f9-112">Virtual members are less forgiving in terms of changes that can be made to them without breaking compatibility.</span></span> <span data-ttu-id="646f9-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span><span class="sxs-lookup"><span data-stu-id="646f9-113">Also, they are slower than non-virtual members, mostly because calls to virtual members are not inlined.</span></span>

 <span data-ttu-id="646f9-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span><span class="sxs-lookup"><span data-stu-id="646f9-114">✔️ CONSIDER limiting extensibility to only what is absolutely necessary.</span></span>

 <span data-ttu-id="646f9-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span><span class="sxs-lookup"><span data-stu-id="646f9-115">✔️ DO prefer protected accessibility over public accessibility for virtual members.</span></span> <span data-ttu-id="646f9-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span><span class="sxs-lookup"><span data-stu-id="646f9-116">Public members should provide extensibility (if required) by calling into a protected virtual member.</span></span>

 <span data-ttu-id="646f9-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span><span class="sxs-lookup"><span data-stu-id="646f9-117">The public members of a class should provide the right set of functionality for direct consumers of that class.</span></span> <span data-ttu-id="646f9-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span><span class="sxs-lookup"><span data-stu-id="646f9-118">Virtual members are designed to be overridden in subclasses, and protected accessibility is a great way to scope all virtual extensibility points to where they can be used.</span></span>

 <span data-ttu-id="646f9-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="646f9-119">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="646f9-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="646f9-120">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="646f9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="646f9-121">See also</span></span>

- [<span data-ttu-id="646f9-122">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="646f9-122">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="646f9-123">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="646f9-123">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
