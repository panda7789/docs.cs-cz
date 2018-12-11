---
title: Operátory rovnosti
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ae188fc7cd55dd843e93afccbe1ea05575a9c36d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129074"
---
# <a name="equality-operators"></a><span data-ttu-id="4560e-102">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="4560e-102">Equality Operators</span></span>
<span data-ttu-id="4560e-103">Tato část popisuje přetížení operátory rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="4560e-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="4560e-104">**X DO NOT** přetížení jeden operátory rovnosti a ne na druhou.</span><span class="sxs-lookup"><span data-stu-id="4560e-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="4560e-105">**✓ DO** Ujistěte se, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti obsahovat přesně stejnou sémantiku a podobné výkonové charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="4560e-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="4560e-106">To často znamená, že `Object.Equals` musí být přepsána, když jsou přetížené operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="4560e-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="4560e-107">**X AVOID** generování výjimek ve operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="4560e-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="4560e-108">Vrátí hodnotu false, pokud jeden z argumentů má hodnotu null namísto vyvolání `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="4560e-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="4560e-109">Operátory rovnosti na hodnotových typech</span><span class="sxs-lookup"><span data-stu-id="4560e-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="4560e-110">**✓ DO** přetížení operátory rovnosti u typů hodnot, pokud má smysl rovnosti.</span><span class="sxs-lookup"><span data-stu-id="4560e-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="4560e-111">Ve většině programovacích jazyků, neexistuje žádný výchozí implementace `operator==` pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="4560e-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="4560e-112">Operátory rovnosti na odkazových typech</span><span class="sxs-lookup"><span data-stu-id="4560e-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="4560e-113">**X AVOID** přetížení operátory rovnosti na proměnlivé odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="4560e-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="4560e-114">Řadu jiných jazyků mají operátory integrované rovnost pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="4560e-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="4560e-115">Integrované operátory obvykle implementují referenční rovnosti a celá řada vývojářů jsou překvapení, když se změní výchozí chování na rovnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="4560e-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="4560e-116">Tento problém je nezměnitelný odkazový typů zmírnit, protože neměnnosti znesnadňuje mnohem Všimněte si rozdílu mezi referenční rovnosti a rovnost hodnot.</span><span class="sxs-lookup"><span data-stu-id="4560e-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="4560e-117">**X AVOID** přetížení operátory rovnosti na odkazových typech Pokud implementace by výrazně pomalejší než referenční rovnosti.</span><span class="sxs-lookup"><span data-stu-id="4560e-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="4560e-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="4560e-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4560e-119">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="4560e-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4560e-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4560e-120">See also</span></span>

- [<span data-ttu-id="4560e-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="4560e-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="4560e-122">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="4560e-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
