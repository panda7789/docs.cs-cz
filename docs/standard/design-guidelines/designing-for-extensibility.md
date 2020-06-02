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
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280241"
---
# <a name="designing-for-extensibility"></a><span data-ttu-id="d89d6-102">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="d89d6-102">Designing for Extensibility</span></span>
<span data-ttu-id="d89d6-103">Jedním z důležitých aspektů návrhu rozhraní je zajistit pečlivě zvážení rozšiřitelnosti rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d89d6-103">One important aspect of designing a framework is making sure the extensibility of the framework has been carefully considered.</span></span> <span data-ttu-id="d89d6-104">To vyžaduje, abyste porozuměli nákladům a výhodám přidruženým k různým mechanismům rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="d89d6-104">This requires that you understand the costs and benefits associated with various extensibility mechanisms.</span></span> <span data-ttu-id="d89d6-105">Tato kapitola vám pomůže určit, který z mechanismů rozšíření – podtříd, události, virtuální členy, zpětná volání a tak dále, mohou nejlépe splňovat požadavky vašeho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d89d6-105">This chapter helps you decide which of the extensibility mechanisms—subclassing, events, virtual members, callbacks, and so on—can best meet the requirements of your framework.</span></span>  
  
 <span data-ttu-id="d89d6-106">Existuje mnoho způsobů, jak v rozhraních zakázat rozšiřitelnost.</span><span class="sxs-lookup"><span data-stu-id="d89d6-106">There are many ways to allow extensibility in frameworks.</span></span> <span data-ttu-id="d89d6-107">Jsou v rozsahu od méně výkonných, ale méně nákladné až po velmi výkonné, ale nákladné.</span><span class="sxs-lookup"><span data-stu-id="d89d6-107">They range from less powerful but less costly to very powerful but expensive.</span></span> <span data-ttu-id="d89d6-108">Pro všechny požadavky na rozšiřitelnost byste měli zvolit nejméně nákladný mechanismus rozšiřitelnosti, který splňuje požadavky.</span><span class="sxs-lookup"><span data-stu-id="d89d6-108">For any given extensibility requirement, you should choose the least costly extensibility mechanism that meets the requirements.</span></span> <span data-ttu-id="d89d6-109">Mějte na paměti, že je obvykle možné přidat další rozšiřitelnost později, ale nemůžete ji nikdy vzít, aniž byste museli zavádět zásadní změny.</span><span class="sxs-lookup"><span data-stu-id="d89d6-109">Keep in mind that it’s usually possible to add more extensibility later, but you can never take it away without introducing breaking changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d89d6-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d89d6-110">In This Section</span></span>  
 [<span data-ttu-id="d89d6-111">Nezapečetěné třídy</span><span class="sxs-lookup"><span data-stu-id="d89d6-111">Unsealed Classes</span></span>](unsealed-classes.md)  
 [<span data-ttu-id="d89d6-112">Chránění členové</span><span class="sxs-lookup"><span data-stu-id="d89d6-112">Protected Members</span></span>](protected-members.md)  
 [<span data-ttu-id="d89d6-113">Události a zpětná volání</span><span class="sxs-lookup"><span data-stu-id="d89d6-113">Events and Callbacks</span></span>](events-and-callbacks.md)  
 [<span data-ttu-id="d89d6-114">Virtuální členové</span><span class="sxs-lookup"><span data-stu-id="d89d6-114">Virtual Members</span></span>](virtual-members.md)  
 [<span data-ttu-id="d89d6-115">Abstrakce (abstraktní typy a rozhraní)</span><span class="sxs-lookup"><span data-stu-id="d89d6-115">Abstractions (Abstract Types and Interfaces)</span></span>](abstractions-abstract-types-and-interfaces.md)  
 [<span data-ttu-id="d89d6-116">Základní třídy pro implementaci abstrakcí</span><span class="sxs-lookup"><span data-stu-id="d89d6-116">Base Classes for Implementing Abstractions</span></span>](base-classes-for-implementing-abstractions.md)  
 [<span data-ttu-id="d89d6-117">Zapečetění</span><span class="sxs-lookup"><span data-stu-id="d89d6-117">Sealing</span></span>](sealing.md)  
 <span data-ttu-id="d89d6-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="d89d6-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d89d6-119">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="d89d6-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89d6-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d89d6-120">See also</span></span>

- [<span data-ttu-id="d89d6-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="d89d6-121">Framework Design Guidelines</span></span>](index.md)
