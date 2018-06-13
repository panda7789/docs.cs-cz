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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 79ca0b92cf79ca9be023925f064c1c7c16b3c9ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567715"
---
# <a name="thread-safety-in-regular-expressions"></a><span data-ttu-id="84195-102">Bezpečnost vlákna v regulárních výrazech</span><span class="sxs-lookup"><span data-stu-id="84195-102">Thread Safety in Regular Expressions</span></span>
<span data-ttu-id="84195-103"><xref:System.Text.RegularExpressions.Regex> Samotné třídy je vlákno bezpečné a neměnné (jen pro čtení).</span><span class="sxs-lookup"><span data-stu-id="84195-103">The <xref:System.Text.RegularExpressions.Regex> class itself is thread safe and immutable (read-only).</span></span> <span data-ttu-id="84195-104">To znamená **Regex** objektů můžete vytvořit z libovolného vlákna a sdílet mezi vlákny; odpovídající metody lze volat z libovolného vlákna a nikdy alter žádný globální stav.</span><span class="sxs-lookup"><span data-stu-id="84195-104">That is, **Regex** objects can be created on any thread and shared between threads; matching methods can be called from any thread and never alter any global state.</span></span>  
  
 <span data-ttu-id="84195-105">Objekty výsledků však (**shodu** a **MatchCollection**) vrácený **Regex** je třeba použít na jedno vlákno.</span><span class="sxs-lookup"><span data-stu-id="84195-105">However, result objects (**Match** and **MatchCollection**) returned by **Regex** should be used on a single thread.</span></span> <span data-ttu-id="84195-106">I když některá z těchto objektů jsou logicky neměnné, jejich implementace by mohla zpozdit výpočty některých výsledků ke zlepšení výkonu a v důsledku toho musí volající serializovat přístup k nim.</span><span class="sxs-lookup"><span data-stu-id="84195-106">Although many of these objects are logically immutable, their implementations could delay computation of some results to improve performance, and as a result, callers must serialize access to them.</span></span>  
  
 <span data-ttu-id="84195-107">Pokud je třeba sdílet **Regex** výsledek objektů na více vláken, tyto objekty lze převést na instancí vláken voláním jejich synchronizovaných metod.</span><span class="sxs-lookup"><span data-stu-id="84195-107">If there is a need to share **Regex** result objects on multiple threads, these objects can be converted to thread-safe instances by calling their synchronized methods.</span></span> <span data-ttu-id="84195-108">Všechny třídy regulárních výrazů s výjimkou výčty, jsou bezpečné pro přístup z více vláken nebo mohou být převedeny na objekty zabezpečenými synchronizované metodou.</span><span class="sxs-lookup"><span data-stu-id="84195-108">With the exception of enumerators, all regular expression classes are thread safe or can be converted into thread-safe objects by a synchronized method.</span></span>  
  
 <span data-ttu-id="84195-109">Výčty jsou jedinou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="84195-109">Enumerators are the only exception.</span></span> <span data-ttu-id="84195-110">Aplikace musí serializovat volání čítačů kolekcí.</span><span class="sxs-lookup"><span data-stu-id="84195-110">An application must serialize calls to collection enumerators.</span></span> <span data-ttu-id="84195-111">Pravidlo je, pokud kolekce, mohou být současně uvedené na více než jedno vlákno, bude třeba synchronizovat metody enumerátor pro kořenový objekt kolekce procházené pomocí čítače.</span><span class="sxs-lookup"><span data-stu-id="84195-111">The rule is that if a collection can be enumerated on more than one thread simultaneously, you should synchronize enumerator methods on the root object of the collection traversed by the enumerator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84195-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="84195-112">See Also</span></span>  
 [<span data-ttu-id="84195-113">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="84195-113">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)
