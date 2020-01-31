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
ms.openlocfilehash: 34fc8eef5270369419b76899f0dbe1ace106caf6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741702"
---
# <a name="equality-operators"></a><span data-ttu-id="358bc-102">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="358bc-102">Equality Operators</span></span>
<span data-ttu-id="358bc-103">Tato část popisuje přetížení operátorů rovnosti a odkazuje na `operator==` a `operator!=` jako operátory rovnosti.</span><span class="sxs-lookup"><span data-stu-id="358bc-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="358bc-104">❌ nepřetížit jeden z operátorů rovnosti a nikoli druhý.</span><span class="sxs-lookup"><span data-stu-id="358bc-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="358bc-105">✔️ se ujistěte, že <xref:System.Object.Equals%2A?displayProperty=nameWithType> a operátory rovnosti mají přesně stejnou sémantiku a podobné charakteristiky výkonu.</span><span class="sxs-lookup"><span data-stu-id="358bc-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="358bc-106">To často znamená, že `Object.Equals` nutné přepsat při přetížení operátorů rovnosti.</span><span class="sxs-lookup"><span data-stu-id="358bc-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="358bc-107">❌ Vyhněte se vyvolávání výjimek z operátorů rovnosti.</span><span class="sxs-lookup"><span data-stu-id="358bc-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="358bc-108">Například vrátí hodnotu false, pokud jeden z argumentů má hodnotu null namísto vyvolání `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="358bc-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="358bc-109">Operátory rovnosti na hodnotových typech</span><span class="sxs-lookup"><span data-stu-id="358bc-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="358bc-110">Pokud je rovnost smysluplná, ✔️ přetížit operátory rovnosti na hodnotových typech.</span><span class="sxs-lookup"><span data-stu-id="358bc-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="358bc-111">Ve většině programovacích jazyků neexistuje žádná výchozí implementace `operator==` pro typy hodnot.</span><span class="sxs-lookup"><span data-stu-id="358bc-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="358bc-112">Operátory rovnosti na odkazových typech</span><span class="sxs-lookup"><span data-stu-id="358bc-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="358bc-113">❌ Vyhněte se přetížení operátorů rovnosti na proměnlivých odkazových typech.</span><span class="sxs-lookup"><span data-stu-id="358bc-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="358bc-114">Mnoho jazyků má předdefinované operátory rovnosti pro typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="358bc-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="358bc-115">Předdefinované operátory obvykle implementují rovnost odkazů a mnoho vývojářů je překvapeno, pokud je výchozí chování změněno na hodnotu rovnosti.</span><span class="sxs-lookup"><span data-stu-id="358bc-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="358bc-116">Tento problém je zmírnit pro neměnný odkazové typy, protože neměnnosti je mnohem obtížnější si všimnout rozdílu mezi rovností odkazů a rovností hodnot.</span><span class="sxs-lookup"><span data-stu-id="358bc-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="358bc-117">❌ se vyhnout přetížení operátorů rovnosti na odkazových typech, pokud by implementace byla výrazně pomalejší než referenční rovnost.</span><span class="sxs-lookup"><span data-stu-id="358bc-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="358bc-118">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="358bc-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="358bc-119">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="358bc-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="358bc-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="358bc-120">See also</span></span>

- [<span data-ttu-id="358bc-121">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="358bc-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="358bc-122">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="358bc-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
