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
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123127"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="57517-102">Postupy: Vytváření předvypočítaných úloh</span><span class="sxs-lookup"><span data-stu-id="57517-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="57517-103">Tento dokument popisuje, jak použít metodu <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="57517-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="57517-104">Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> vrátí dokončený objekt <xref:System.Threading.Tasks.Task%601>, který obsahuje poskytnutou hodnotu jako vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A>.</span><span class="sxs-lookup"><span data-stu-id="57517-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="57517-105">Tato metoda je užitečná při provádění asynchronní operace, která vrací objekt <xref:System.Threading.Tasks.Task%601> a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán.</span><span class="sxs-lookup"><span data-stu-id="57517-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57517-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="57517-106">Example</span></span>  
 <span data-ttu-id="57517-107">Následující příklad stahuje řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="57517-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="57517-108">Definuje metodu `DownloadStringAsync`.</span><span class="sxs-lookup"><span data-stu-id="57517-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="57517-109">Tato metoda stahuje řetězce z webu asynchronně.</span><span class="sxs-lookup"><span data-stu-id="57517-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="57517-110">Tento příklad také používá objekt <xref:System.Collections.Concurrent.ConcurrentDictionary%602> k ukládání výsledků předchozích operací do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="57517-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="57517-111">Pokud je vstupní adresa uložena v této mezipaměti, `DownloadStringAsync` používá metodu <xref:System.Threading.Tasks.Task.FromResult%2A> k vytvoření <xref:System.Threading.Tasks.Task%601> objektu, který obsahuje obsah na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="57517-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="57517-112">V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidá výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="57517-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="57517-113">Tento příklad vypočítá čas, který je vyžadován ke stažení více řetězců dvakrát.</span><span class="sxs-lookup"><span data-stu-id="57517-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="57517-114">Druhá sada operací stahování by měla trvat kratší dobu než první sada, protože výsledky jsou uchovávány v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="57517-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="57517-115">Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> umožňuje, aby metoda `DownloadStringAsync` vytvořila objekty <xref:System.Threading.Tasks.Task%601>, které obsahují tyto předem vypočítané výsledky.</span><span class="sxs-lookup"><span data-stu-id="57517-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57517-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57517-116">See also</span></span>

- [<span data-ttu-id="57517-117">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="57517-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
