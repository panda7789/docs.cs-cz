---
title: 'Postupy: Vytváření předvypočítaných úloh'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e68465b6fae39089600457414e7f2a2328f725b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593133"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="46749-102">Postupy: Vytváření předvypočítaných úloh</span><span class="sxs-lookup"><span data-stu-id="46749-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="46749-103">Tento dokument popisuje způsob použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody k načtení výsledků asynchronní operací stažení, které jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="46749-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="46749-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda vrátí dokončení <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadaná hodnota jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="46749-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="46749-105">Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán.</span><span class="sxs-lookup"><span data-stu-id="46749-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46749-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="46749-106">Example</span></span>  
 <span data-ttu-id="46749-107">Následující příklad stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="46749-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="46749-108">Definuje `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="46749-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="46749-109">Tato metoda asynchronně stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="46749-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="46749-110">Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objektu pro ukládání do mezipaměti výsledky předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="46749-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="46749-111">Pokud je vstupní adresu je uložena v mezipaměti, `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metodu za účelem vytvoření <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje obsah na této adrese.</span><span class="sxs-lookup"><span data-stu-id="46749-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="46749-112">V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidává výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="46749-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="46749-113">Tento příklad zjistí čas, který je potřeba ke stahování vícenásobných řetězců dvakrát.</span><span class="sxs-lookup"><span data-stu-id="46749-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="46749-114">Druhou sadu operací stažení by měla trvat kratší dobu než první sady, protože výsledky jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="46749-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="46749-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umožňuje `DownloadStringAsync` metodu pro vytvoření <xref:System.Threading.Tasks.Task%601> objekty, které obsahují tyto předem vypočítané výsledky.</span><span class="sxs-lookup"><span data-stu-id="46749-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46749-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46749-116">See also</span></span>

- [<span data-ttu-id="46749-117">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="46749-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
