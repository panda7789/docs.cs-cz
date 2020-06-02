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
ms.openlocfilehash: fbcaaf4942f8af1d6c1de52ff5bc11317318f319
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290886"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="ea284-102">Bezpečnost vlákna v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="ea284-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="ea284-103"><xref:System.Text.RegularExpressions.Regex>Samotná třída je vláknově bezpečná a neměnná (jen pro čtení).</span><span class="sxs-lookup"><span data-stu-id="ea284-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="ea284-104">To znamená, že objekty **Regex** lze vytvořit v jakémkoli vlákně a sdílet je mezi vlákny. metody porovnání mohou být volány z libovolného vlákna a nikdy nemění žádný globální stav.</span><span class="sxs-lookup"><span data-stu-id="ea284-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="ea284-105">Nicméně objekty výsledků (**Match** a **MatchCollection**) vrácené **výrazem Regex** by měly být použity v jednom vlákně.</span><span class="sxs-lookup"><span data-stu-id="ea284-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="ea284-106">I když je mnoho z těchto objektů logicky neměnný, jejich implementace mohou zpozdit výpočet některých výsledků za účelem zvýšení výkonu, a v důsledku toho volající musí serializovat přístup.</span><span class="sxs-lookup"><span data-stu-id="ea284-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="ea284-107">Pokud je nutné sdílet objekty výsledků **regulárního výrazu** ve více vláknech, lze tyto objekty převést na instance bezpečné pro přístup z více vláken voláním jejich synchronizovaných metod.</span><span class="sxs-lookup"><span data-stu-id="ea284-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="ea284-108">S výjimkou enumerátorů jsou všechny třídy regulárních výrazů bezpečné pro přístup z více vláken nebo mohou být převedeny na objekty bezpečné pro přístup z více vláken synchronizované metodou.</span><span class="sxs-lookup"><span data-stu-id="ea284-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="ea284-109">Enumerátory jsou jedinou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="ea284-109">Enumerators are the only exception.</span></span> <span data-ttu-id="ea284-110">Aplikace musí serializovat volání enumerátorů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="ea284-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="ea284-111">Pravidlem je, že pokud kolekci lze vytvořit ve více než jednom vlákně, je třeba synchronizovat metody enumerátoru v kořenovém objektu kolekce prochází enumerátorem.</span><span class="sxs-lookup"><span data-stu-id="ea284-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea284-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea284-112">See also</span></span>

- [<span data-ttu-id="ea284-113">Regulární výrazy .NET</span><span class="sxs-lookup"><span data-stu-id="ea284-113">.NET Regular Expressions</span></span>](regular-expressions.md)
