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
ms.openlocfilehash: 88f0782380d21858bc5dd0fc0fbf63bbf85403b8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289990"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="b19f7-102">Postupy: Vytváření předvypočítaných úloh</span><span class="sxs-lookup"><span data-stu-id="b19f7-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="b19f7-103">Tento dokument popisuje, jak použít <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metodu k načtení výsledků asynchronních operací stažení, které jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b19f7-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="b19f7-104"><xref:System.Threading.Tasks.Task.FromResult%2A>Metoda vrátí dokončený <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje poskytnutou hodnotu jako <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b19f7-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="b19f7-105">Tato metoda je užitečná při provádění asynchronní operace, která vrací <xref:System.Threading.Tasks.Task%601> objekt a výsledek tohoto <xref:System.Threading.Tasks.Task%601> objektu je již vypočítán.</span><span class="sxs-lookup"><span data-stu-id="b19f7-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b19f7-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b19f7-106">Example</span></span>  
 <span data-ttu-id="b19f7-107">Následující příklad stahuje řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="b19f7-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="b19f7-108">Definuje `DownloadStringAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="b19f7-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="b19f7-109">Tato metoda stahuje řetězce z webu asynchronně.</span><span class="sxs-lookup"><span data-stu-id="b19f7-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="b19f7-110">Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekt k ukládání výsledků předchozích operací do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b19f7-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="b19f7-111">Pokud je vstupní adresa uložena v této mezipaměti, `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metodu k vytvoření <xref:System.Threading.Tasks.Task%601> objektu, který obsahuje obsah na dané adrese.</span><span class="sxs-lookup"><span data-stu-id="b19f7-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="b19f7-112">V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidá výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b19f7-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="b19f7-113">Tento příklad vypočítá čas, který je vyžadován ke stažení více řetězců dvakrát.</span><span class="sxs-lookup"><span data-stu-id="b19f7-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="b19f7-114">Druhá sada operací stahování by měla trvat kratší dobu než první sada, protože výsledky jsou uchovávány v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="b19f7-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="b19f7-115"><xref:System.Threading.Tasks.Task.FromResult%2A>Metoda umožňuje `DownloadStringAsync` metodě vytvářet <xref:System.Threading.Tasks.Task%601> objekty, které obsahují tyto předem vypočítané výsledky.</span><span class="sxs-lookup"><span data-stu-id="b19f7-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b19f7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b19f7-116">See also</span></span>

- [<span data-ttu-id="b19f7-117">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="b19f7-117">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
