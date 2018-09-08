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
ms.openlocfilehash: 47e4c5d721b37388a4008d100f5212057477c638
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44211655"
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="63541-102">Postupy: Vytváření předvypočítaných úloh</span><span class="sxs-lookup"><span data-stu-id="63541-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="63541-103">Tento dokument popisuje způsob použití <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> metody k načtení výsledků asynchronní operací stažení, které jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="63541-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="63541-104"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda vrátí dokončení <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje zadaná hodnota jako jeho <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="63541-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="63541-105">Tato metoda je užitečná při provádění asynchronní operace, která vrátí <xref:System.Threading.Tasks.Task%601> objektu a výsledek tohoto objektu <xref:System.Threading.Tasks.Task%601> již je vypočítán.</span><span class="sxs-lookup"><span data-stu-id="63541-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63541-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="63541-106">Example</span></span>  
 <span data-ttu-id="63541-107">Následující příklad stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="63541-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="63541-108">Definuje `DownloadStringAsync` metody.</span><span class="sxs-lookup"><span data-stu-id="63541-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="63541-109">Tato metoda asynchronně stáhne řetězce z webu.</span><span class="sxs-lookup"><span data-stu-id="63541-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="63541-110">Tento příklad také používá <xref:System.Collections.Concurrent.ConcurrentDictionary%602> objektu pro ukládání do mezipaměti výsledky předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="63541-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="63541-111">Pokud je vstupní adresu je uložena v mezipaměti, `DownloadStringAsync` používá <xref:System.Threading.Tasks.Task.FromResult%2A> metodu za účelem vytvoření <xref:System.Threading.Tasks.Task%601> objekt, který obsahuje obsah na této adrese.</span><span class="sxs-lookup"><span data-stu-id="63541-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="63541-112">V opačném případě `DownloadStringAsync` stáhne soubor z webu a přidává výsledek do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="63541-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="63541-113">Tento příklad zjistí čas, který je potřeba ke stahování vícenásobných řetězců dvakrát.</span><span class="sxs-lookup"><span data-stu-id="63541-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="63541-114">Druhou sadu operací stažení by měla trvat kratší dobu než první sady, protože výsledky jsou uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="63541-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="63541-115"><xref:System.Threading.Tasks.Task.FromResult%2A> Metoda umožňuje `DownloadStringAsync` metodu pro vytvoření <xref:System.Threading.Tasks.Task%601> objekty, které obsahují tyto předem vypočítané výsledky.</span><span class="sxs-lookup"><span data-stu-id="63541-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63541-116">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="63541-116">Compiling the Code</span></span>  
 <span data-ttu-id="63541-117">Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `CachedDownloads.cs` (`CachedDownloads.vb` v jazyce Visual Basic), a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63541-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for Visual Basic), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 <span data-ttu-id="63541-118">Visual C#</span><span class="sxs-lookup"><span data-stu-id="63541-118">Visual C#</span></span>  
  
 <span data-ttu-id="63541-119">**csc.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="63541-119">**csc.exe CachedDownloads.cs**</span></span>  
  
 <span data-ttu-id="63541-120">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63541-120">Visual Basic</span></span>  
  
 <span data-ttu-id="63541-121">**Vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="63541-121">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="63541-122">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="63541-122">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63541-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63541-123">See also</span></span>

- [<span data-ttu-id="63541-124">Asynchronní programování založené na úlohách</span><span class="sxs-lookup"><span data-stu-id="63541-124">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
