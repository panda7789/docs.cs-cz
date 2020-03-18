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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123127"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="cef6b-102">Postupy: Vytváření předvypočítaných úloh</span><span class="sxs-lookup"><span data-stu-id="cef6b-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="cef6b-103">Tento dokument popisuje, jak <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> použít metodu k načtení výsledků asynchronní operace stahování, které jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cef6b-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="cef6b-104">Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> vrátí hotový <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadali hodnotu jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cef6b-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="cef6b-105">Tato metoda je užitečná, když provedete asynchronní operaci, která vrátí <xref:System.Threading.Tasks.Task%601> objekt a výsledek tohoto <xref:System.Threading.Tasks.Task%601> objektu je již vypočítán.</span><span class="sxs-lookup"><span data-stu-id="cef6b-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cef6b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cef6b-106">Example</span></span>  
 <span data-ttu-id="cef6b-107">Následující příklad stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="cef6b-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="cef6b-108">Definuje metodu. `DownloadStringAsync`</span><span class="sxs-lookup"><span data-stu-id="cef6b-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="cef6b-109">Tato metoda stahuje řetězce z webu asynchronně.</span><span class="sxs-lookup"><span data-stu-id="cef6b-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="cef6b-110">Tento příklad také <xref:System.Collections.Concurrent.ConcurrentDictionary%602> používá objekt do mezipaměti výsledky předchozích operací.</span><span class="sxs-lookup"><span data-stu-id="cef6b-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="cef6b-111">Pokud je vstupní adresa uložena `DownloadStringAsync` v <xref:System.Threading.Tasks.Task.FromResult%2A> této mezipaměti, používá metodu k vytvoření objektu, <xref:System.Threading.Tasks.Task%601> který obsahuje obsah na této adrese.</span><span class="sxs-lookup"><span data-stu-id="cef6b-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="cef6b-112">V `DownloadStringAsync` opačném případě stáhne soubor z webu a přidá výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cef6b-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="cef6b-113">Tento příklad vypočítá čas, který je nutný ke stažení více řetězců dvakrát.</span><span class="sxs-lookup"><span data-stu-id="cef6b-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="cef6b-114">Druhá sada operací stahování by měla trvat kratší dobu než první sada, protože výsledky jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="cef6b-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="cef6b-115">Metoda <xref:System.Threading.Tasks.Task.FromResult%2A> umožňuje `DownloadStringAsync` metodu <xref:System.Threading.Tasks.Task%601> vytvořit objekty, které drží tyto předem vypočítané výsledky.</span><span class="sxs-lookup"><span data-stu-id="cef6b-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef6b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cef6b-116">See also</span></span>

- [<span data-ttu-id="cef6b-117">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="cef6b-117">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
