---
title: Bezpečnost vlákna v regulárních výrazech
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework regular expressions, threads
- regular expressions, threads
- searching with regular expressions, threads
- parsing text with regular expressions, threads
- pattern-matching with regular expressions, threads
ms.assetid: 7c4a167b-5236-4cde-a2ca-58646230730f
ms.openlocfilehash: db25028e10872cfca08d28518c795414d06c5d49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73124802"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="49145-102">Bezpečnost vlákna v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="49145-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="49145-103">Třída <xref:System.Text.RegularExpressions.Regex> sama o sobě je bezpečné pro přístup z více vláken a neměnné (jen pro čtení).</span><span class="sxs-lookup"><span data-stu-id="49145-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="49145-104">To znamená, **že objekty Regex** lze vytvořit v libovolném vlákně a sdílet mezi podprocesy; odpovídající metody lze volat z libovolného vlákna a nikdy měnit žádný globální stav.</span><span class="sxs-lookup"><span data-stu-id="49145-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="49145-105">Však result objekty **(Match** a **MatchCollection**) vrácené **Regex** by měly být použity na jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="49145-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="49145-106">Přestože mnoho z těchto objektů jsou logicky neměnné, jejich implementace může zpozdit výpočtu některých výsledků ke zlepšení výkonu a v důsledku toho volající musí serializovat přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="49145-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="49145-107">Pokud je potřeba sdílet objekty **výsledků Regex** ve více vláknech, tyto objekty lze převést na instance bezpečné pro přístup z více vláken voláním jejich synchronizované metody.</span><span class="sxs-lookup"><span data-stu-id="49145-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="49145-108">S výjimkou čítačů jsou všechny třídy regulárních výrazů bezpečné pro přístup z více vláken nebo mohou být synchronizovány na objekty bezpečné pro přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="49145-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="49145-109">Výčty jsou jedinou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="49145-109">Enumerators are the only exception.</span></span> <span data-ttu-id="49145-110">Aplikace musí serializovat volání čítače výčtu kolekce.</span><span class="sxs-lookup"><span data-stu-id="49145-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="49145-111">Pravidlo je, že pokud kolekce může být výčtu na více než jeden podproces současně, měli byste synchronizovat metody výčtu na kořenový objekt kolekce provázána čítače.</span><span class="sxs-lookup"><span data-stu-id="49145-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49145-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="49145-112">See also</span></span>

- [<span data-ttu-id="49145-113">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="49145-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
