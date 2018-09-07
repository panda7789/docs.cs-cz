---
title: Navrhování pro rozšiřitelnost
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44080979"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="2008a-102">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="2008a-102">Designing for Extensibility</span></span>
<span data-ttu-id="2008a-103">Jeden důležitý aspekt návrhu rozhraní, je zajistit, že pečlivě zvážit rozšíření rozhraní framework.</span><span class="sxs-lookup"><span data-stu-id="2008a-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="2008a-104">Tento postup vyžaduje, že rozumíte nákladů a přínosů přidružené různé mechanismy rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="2008a-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="2008a-105">Tato kapitola vám pomůže rozhodnout, které mechanismus rozšíření – vytváření podtříd, události, virtuální členy, zpětná volání a tak dále – můžete nejlíp vyhovovat požadavkům vaší architektury.</span><span class="sxs-lookup"><span data-stu-id="2008a-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="2008a-106">Existuje mnoho způsobů, jak povolit rozšíření v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2008a-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="2008a-107">Jsou v rozsahu od méně efektivní, ale levnějších do velmi výkonné, ale drahé.</span><span class="sxs-lookup"><span data-stu-id="2008a-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="2008a-108">Pro všechny požadavky dané rozšíření měli byste vybrat minimální nákladnou mechanismus rozšiřitelnosti, který splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="2008a-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="2008a-109">Mějte na paměti, že je obvykle možné případná další rozšíření později, ale nikdy udělat to okamžitě bez vnášení nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="2008a-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2008a-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2008a-110">In This Section</span></span>  
 [<span data-ttu-id="2008a-111">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="2008a-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="2008a-112">Chráněné členy</span><span class="sxs-lookup"><span data-stu-id="2008a-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="2008a-113">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="2008a-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="2008a-114">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="2008a-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="2008a-115">Abstrakce (abstraktní typy a rozhraní)</span><span class="sxs-lookup"><span data-stu-id="2008a-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="2008a-116">Základní třídy pro implementaci abstrakcí</span><span class="sxs-lookup"><span data-stu-id="2008a-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="2008a-117">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="2008a-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="2008a-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="2008a-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2008a-119">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="2008a-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2008a-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2008a-120">See also</span></span>

- [<span data-ttu-id="2008a-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="2008a-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
