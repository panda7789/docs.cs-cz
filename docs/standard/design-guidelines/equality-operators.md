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
ms.openlocfilehash: 31a5ce18f4526b5e3b8411365dff812601de87ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709436"
---
# <a name="equality-operators"></a><span data-ttu-id="e5221-102">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="e5221-102">Equality Operators</span></span>
<span data-ttu-id="e5221-103">Tato část popisuje přetížení operátorů rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e5221-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="e5221-104">**X DO NOT** přetížení jeden operátory rovnosti a ne na druhou.</span><span class="sxs-lookup"><span data-stu-id="e5221-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="e5221-105">**✓ DO** Ujistěte se, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti obsahovat přesně stejnou sémantiku a podobné výkonové charakteristiky.</span><span class="sxs-lookup"><span data-stu-id="e5221-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="e5221-106">To často znamená, že `Object.Equals` nutné přepsat při přetížení operátorů rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e5221-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="e5221-107">**X AVOID** generování výjimek ve operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e5221-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="e5221-108">Například vrátí hodnotu false, pokud jeden z argumentů má hodnotu null namísto vyvolání `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="e5221-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="e5221-109">Operátory rovnosti na hodnotových typech</span><span class="sxs-lookup"><span data-stu-id="e5221-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="e5221-110">**✓ DO** přetížení operátory rovnosti u typů hodnot, pokud má smysl rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e5221-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="e5221-111">Ve většině programovacích jazyků neexistuje žádná výchozí implementace `operator==` pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="e5221-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="e5221-112">Operátory rovnosti na odkazových typech</span><span class="sxs-lookup"><span data-stu-id="e5221-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="e5221-113">**X AVOID** přetížení operátory rovnosti na proměnlivé odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="e5221-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="e5221-114">Mnoho jazyků má předdefinované operátory rovnosti pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="e5221-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="e5221-115">Předdefinované operátory obvykle implementují rovnost odkazů a mnoho vývojářů je překvapeno, pokud je výchozí chování změněno na hodnotu rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e5221-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="e5221-116">Tento problém je zmírnit pro neměnný odkazové typy, protože neměnnosti je mnohem obtížnější si všimnout rozdílu mezi rovností odkazů a rovností hodnot.</span><span class="sxs-lookup"><span data-stu-id="e5221-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="e5221-117">**X AVOID** přetížení operátory rovnosti na odkazových typech Pokud implementace by výrazně pomalejší než referenční rovnosti.</span><span class="sxs-lookup"><span data-stu-id="e5221-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="e5221-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="e5221-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e5221-119">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="e5221-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5221-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5221-120">See also</span></span>

- [<span data-ttu-id="e5221-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="e5221-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="e5221-122">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="e5221-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
