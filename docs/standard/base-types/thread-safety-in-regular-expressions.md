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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124802"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="e63e6-102">Bezpečnost vlákna v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="e63e6-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="e63e6-103">Samotná třída <xref:System.Text.RegularExpressions.Regex> je vláknově bezpečná a neměnná (jen pro čtení).</span><span class="sxs-lookup"><span data-stu-id="e63e6-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="e63e6-104">To znamená, že objekty **Regex** lze vytvořit v jakémkoli vlákně a sdílet je mezi vlákny. metody porovnání mohou být volány z libovolného vlákna a nikdy nemění žádný globální stav.</span><span class="sxs-lookup"><span data-stu-id="e63e6-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="e63e6-105">Nicméně objekty výsledků (**Match** a **MatchCollection**) vrácené **výrazem Regex** by měly být použity v jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="e63e6-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="e63e6-106">I když je mnoho z těchto objektů logicky neměnný, jejich implementace mohou zpozdit výpočet některých výsledků za účelem zvýšení výkonu, a v důsledku toho volající musí serializovat přístup.</span><span class="sxs-lookup"><span data-stu-id="e63e6-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="e63e6-107">Pokud je nutné sdílet objekty výsledků **regulárního výrazu** ve více vláknech, lze tyto objekty převést na instance bezpečné pro přístup z více vláken voláním jejich synchronizovaných metod.</span><span class="sxs-lookup"><span data-stu-id="e63e6-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="e63e6-108">S výjimkou enumerátorů jsou všechny třídy regulárních výrazů bezpečné pro přístup z více vláken nebo mohou být převedeny na objekty bezpečné pro přístup z více vláken synchronizované metodou.</span><span class="sxs-lookup"><span data-stu-id="e63e6-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="e63e6-109">Enumerátory jsou jedinou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="e63e6-109">Enumerators are the only exception.</span></span> <span data-ttu-id="e63e6-110">Aplikace musí serializovat volání enumerátorů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="e63e6-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="e63e6-111">Pravidlem je, že pokud kolekci lze vytvořit ve více než jednom vlákně, je třeba synchronizovat metody enumerátoru v kořenovém objektu kolekce prochází enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="e63e6-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63e6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e63e6-112">See also</span></span>

- [<span data-ttu-id="e63e6-113">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="e63e6-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
