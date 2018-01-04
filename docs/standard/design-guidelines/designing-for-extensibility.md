---
title: "Navrhování pro rozšiřitelnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f21e9239199ecd36432ed8f14adb896f1799506b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="c26a8-102">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="c26a8-102">Designing for Extensibility</span></span>
<span data-ttu-id="c26a8-103">Jeden důležitým aspektem navrhování rozhraní je Ujistěte se, že pečlivě zvážit rozšiřitelnost rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="c26a8-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="c26a8-104">To vyžaduje, abyste rozuměli tomu náklady a výhod spojených s různé mechanismy pro rozšíření.</span><span class="sxs-lookup"><span data-stu-id="c26a8-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="c26a8-105">Tato kapitola vám pomůže zjistit, které mechanismů rozšíření – vytváření podtříd, události, virtuální členové, zpětná volání a tak dále – nejlépe splňují požadavky vašeho prostředí.</span><span class="sxs-lookup"><span data-stu-id="c26a8-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="c26a8-106">Existuje mnoho způsobů tak, aby měl rozšiřitelnost rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c26a8-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="c26a8-107">Budou v rozsahu od méně efektivní, ale levněji k velmi výkonné, ale nákladná.</span><span class="sxs-lookup"><span data-stu-id="c26a8-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="c26a8-108">Každý požadavek dané rozšíření měli byste vybrat alespoň nákladná mechanismus rozšiřitelnosti, který splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="c26a8-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="c26a8-109">Uvědomte si, že je obvykle možné později přidat další rozšíření, ale nikdy vám ji rychle bez zavedení nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="c26a8-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c26a8-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="c26a8-110">In This Section</span></span>  
 [<span data-ttu-id="c26a8-111">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="c26a8-111">Unsealed Classes</span></span>](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [<span data-ttu-id="c26a8-112">Chráněné členy</span><span class="sxs-lookup"><span data-stu-id="c26a8-112">Protected Members</span></span>](../../../docs/standard/design-guidelines/protected-members.md)  
 [<span data-ttu-id="c26a8-113">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="c26a8-113">Events and Callbacks</span></span>](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [<span data-ttu-id="c26a8-114">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="c26a8-114">Virtual Members</span></span>](../../../docs/standard/design-guidelines/virtual-members.md)  
 [<span data-ttu-id="c26a8-115">Abstrakce (abstraktní typy a rozhraní)</span><span class="sxs-lookup"><span data-stu-id="c26a8-115">Abstractions (Abstract Types and Interfaces)</span></span>](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="c26a8-116">Základní třídy pro implementaci abstrakcí</span><span class="sxs-lookup"><span data-stu-id="c26a8-116">Base Classes for Implementing Abstractions</span></span>](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="c26a8-117">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="c26a8-117">Sealing</span></span>](../../../docs/standard/design-guidelines/sealing.md)  
 <span data-ttu-id="c26a8-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="c26a8-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c26a8-119">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="c26a8-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26a8-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="c26a8-120">See Also</span></span>  
 [<span data-ttu-id="c26a8-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="c26a8-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
