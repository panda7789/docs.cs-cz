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
ms.openlocfilehash: d5d688041c6a8947b4a30f067d969cb6cb3bbf0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583900"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="ffd7d-102">Postupy: Vytváření předvypočítaných úloh</span><span class="sxs-lookup"><span data-stu-id="ffd7d-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="ffd7d-103">Tento dokument popisuje postup použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metoda načíst výsledky stahování asynchronní operace, které jsou uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="ffd7d-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda vrátí dokončení <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadaná hodnota jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="ffd7d-105">Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek této <xref:System.Threading.Tasks.Task%601> objektu již je počítaný.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffd7d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffd7d-106">Example</span></span>  
 <span data-ttu-id="ffd7d-107">Následující příklad stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="ffd7d-108">Definuje, `DownloadStringAsync` metoda.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="ffd7d-109">Tato metoda asynchronně stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="ffd7d-110">Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objekt pro ukládání do mezipaměti výsledky předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="ffd7d-111">Pokud je v této mezipaměti adresu vstupní `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metoda k vytvoření <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje obsah na této adrese.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="ffd7d-112">V opačném `DownloadStringAsync` stáhne soubor z webu a přidává výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="ffd7d-113">Tento příklad vypočítá čas, které je nutné stáhnout vícenásobných řetězců dvakrát.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="ffd7d-114">Druhá sada stažení operace by měla trvat kratší dobu, než první sady, protože výsledky jsou uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="ffd7d-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umožňuje `DownloadStringAsync` metodu pro vytvoření <xref:System.Threading.Tasks.Task%601> objekty, které mají tyto předvypočítaných výsledky.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ffd7d-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ffd7d-116">Compiling the Code</span></span>  
 <span data-ttu-id="ffd7d-117">Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `CachedDownloads.cs` (`CachedDownloads.vb` jazyka Visual Basic), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="ffd7d-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="ffd7d-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="ffd7d-118">Visual C#</span></span>  
  
 <span data-ttu-id="ffd7d-119">**csc.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="ffd7d-119">**csc.exe CachedDownloads.cs**</span></span>  
  
 <span data-ttu-id="ffd7d-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ffd7d-120">Visual Basic</span></span>  
  
 <span data-ttu-id="ffd7d-121">**Vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="ffd7d-121">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ffd7d-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ffd7d-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffd7d-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffd7d-123">See Also</span></span>  
 [<span data-ttu-id="ffd7d-124">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="ffd7d-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
