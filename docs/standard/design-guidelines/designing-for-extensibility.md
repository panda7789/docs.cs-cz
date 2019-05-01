---
title: Navrhování pro rozšiřitelnost
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: KrzysztofCwalina
ms.openlocfilehash: 94900dee72230a1b9d099d78168acc508af62af7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026455"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="2dbe9-102">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="2dbe9-102">Designing for Extensibility</span></span>
<span data-ttu-id="2dbe9-103">Jeden důležitý aspekt návrhu rozhraní, je zajistit, že pečlivě zvážit rozšíření rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="2dbe9-104">Tento postup vyžaduje, že rozumíte nákladů a přínosů přidružené různé mechanismy rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="2dbe9-105">Tato kapitola vám pomůže rozhodnout, které mechanismus rozšíření – vytváření podtříd, události, virtuální členy, zpětná volání a tak dále – můžete nejlíp vyhovovat požadavkům vaší architektury.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="2dbe9-106">Existuje mnoho způsobů, jak povolit rozšíření v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="2dbe9-107">Jsou v rozsahu od méně efektivní, ale levnějších do velmi výkonné, ale drahé.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="2dbe9-108">Pro všechny požadavky dané rozšíření měli byste vybrat minimální nákladnou mechanismus rozšiřitelnosti, který splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="2dbe9-109">Mějte na paměti, že je obvykle možné případná další rozšíření později, ale nikdy udělat to okamžitě bez vnášení nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="2dbe9-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2dbe9-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2dbe9-110">In This Section</span></span>  
 [<span data-ttu-id="2dbe9-111">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="2dbe9-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="2dbe9-112">Chráněné členy</span><span class="sxs-lookup"><span data-stu-id="2dbe9-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="2dbe9-113">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="2dbe9-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="2dbe9-114">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="2dbe9-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="2dbe9-115">Abstrakce (abstraktní typy a rozhraní)</span><span class="sxs-lookup"><span data-stu-id="2dbe9-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="2dbe9-116">Základní třídy pro implementaci abstrakcí</span><span class="sxs-lookup"><span data-stu-id="2dbe9-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="2dbe9-117">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="2dbe9-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="2dbe9-118">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="2dbe9-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2dbe9-119">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="2dbe9-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dbe9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2dbe9-120">See also</span></span>

- [<span data-ttu-id="2dbe9-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="2dbe9-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
