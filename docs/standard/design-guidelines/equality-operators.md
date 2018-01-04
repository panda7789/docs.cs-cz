---
title: "Operátory rovnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5aa37d2ee6b3b18d9decbc98bd1c427168e8ab35
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="equality-operators"></a><span data-ttu-id="9e857-102">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="9e857-102">Equality Operators</span></span>
<span data-ttu-id="9e857-103">Tato část popisuje přetížení operátory rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="9e857-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="9e857-104">**X nesmí** přetížení jeden operátory rovnosti a ne na druhou.</span><span class="sxs-lookup"><span data-stu-id="9e857-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="9e857-105">**PROVEĎTE ✓** Ujistěte se, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti obsahovat přesně stejnou sémantiku a podobné výkonové charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="9e857-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="9e857-106">To často znamená, že `Object.Equals` musí být potlačena, pokud jsou přetížené operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="9e857-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="9e857-107">**X nepoužívejte** generování výjimek ve operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="9e857-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="9e857-108">Vrátí hodnotu false, pokud jeden z argumentů hodnotu null místo vyvolání `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="9e857-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="9e857-109">Operátory rovnosti u typů hodnot</span><span class="sxs-lookup"><span data-stu-id="9e857-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="9e857-110">**PROVEĎTE ✓** přetížení operátory rovnosti u typů hodnot, pokud má smysl rovnosti.</span><span class="sxs-lookup"><span data-stu-id="9e857-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="9e857-111">Ve většině programovacích jazyků, neexistuje žádný výchozí implementaci třídy `operator==` u typů hodnot.</span><span class="sxs-lookup"><span data-stu-id="9e857-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="9e857-112">Operátory rovnosti na odkazových typech</span><span class="sxs-lookup"><span data-stu-id="9e857-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="9e857-113">**X nepoužívejte** přetížení operátory rovnosti na proměnlivé odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="9e857-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="9e857-114">Mnoho jazyky mají operátory rovnosti předdefinované pro odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="9e857-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="9e857-115">Předdefinované operátory obvykle implementovat referenční rovnosti a když se změní výchozí chování na rovnosti hodnoty překvapil celá řada vývojářů.</span><span class="sxs-lookup"><span data-stu-id="9e857-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="9e857-116">Protože neměnitelnosti znesnadňuje mnohem Všimněte rozdíl mezi referenční rovnosti a rovnosti hodnoty pro neměnné odkazové typy zmírnit tento problém.</span><span class="sxs-lookup"><span data-stu-id="9e857-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="9e857-117">**X nepoužívejte** přetížení operátory rovnosti na odkazových typech Pokud implementace by výrazně pomalejší než referenční rovnosti.</span><span class="sxs-lookup"><span data-stu-id="9e857-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="9e857-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="9e857-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9e857-119">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="9e857-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e857-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e857-120">See Also</span></span>  
 [<span data-ttu-id="9e857-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="9e857-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="9e857-122">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="9e857-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
