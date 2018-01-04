---
title: "Postupy: Naslouchání požadavkům zrušení dotazováním"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56a927e10cb026814302728a72acb2f32223b29b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="5c52a-102">Postupy: Naslouchání požadavkům zrušení dotazováním</span><span class="sxs-lookup"><span data-stu-id="5c52a-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="5c52a-103">Následující příklad ukazuje jeden ze způsobů, který uživatelského kódu můžete dotazovat token zrušení v pravidelných intervalech zobrazíte zrušení požádal z volající vlákno.</span><span class="sxs-lookup"><span data-stu-id="5c52a-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="5c52a-104">Tento příklad používá <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typ, ale stejného vzoru platí pro asynchronní operace, které jsou vytvořené přímo pomocí <xref:System.Threading.ThreadPool?displayProperty=nameWithType> typu nebo <xref:System.Threading.Thread?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="5c52a-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c52a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c52a-105">Example</span></span>  
 <span data-ttu-id="5c52a-106">Dotazování vyžaduje nějaký druh smyčky nebo rekurzivní kód, který může číst pravidelně hodnota logická hodnota <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5c52a-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="5c52a-107">Pokud používáte <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> typu a čekají na dokončení na volající vlákno úlohy, můžete použít <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metodu pro kontrolu vlastnosti a vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="5c52a-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="5c52a-108">Pomocí této metody je zajistit, že je správný výjimka vydána v reakci na žádost.</span><span class="sxs-lookup"><span data-stu-id="5c52a-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="5c52a-109">Pokud používáte <xref:System.Threading.Tasks.Task>, pak voláním této metody je lepší, než ručně vyvolání <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="5c52a-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="5c52a-110">Pokud nemáte má být vyvolána výjimka, pak právě Zkontrolujte vlastnost a vrátit z metody, pokud je vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="5c52a-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="5c52a-111">Volání metody <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> je velmi rychlý a nezavádí významné režijní náklady v smyčky.</span><span class="sxs-lookup"><span data-stu-id="5c52a-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="5c52a-112">Při volání <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, budete muset explicitně zkontrolovala <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost, pokud máte jinou práci udělat v reakci na zrušení kromě způsobující výjimku.</span><span class="sxs-lookup"><span data-stu-id="5c52a-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="5c52a-113">V tomto příkladu vidíte, že kód ve skutečnosti přistupuje k vlastnosti dvakrát: jednou v výslovný přístup a znovu v <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="5c52a-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="5c52a-114">Ale protože v rámci čtení <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> vlastnost zahrnuje pouze jeden volatile instrukce za přístup pro čtení, double přístup není významné z hlediska výkonu.</span><span class="sxs-lookup"><span data-stu-id="5c52a-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="5c52a-115">Je stále vhodnější volat metodu než ručně throw <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="5c52a-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c52a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c52a-116">See Also</span></span>  
 [<span data-ttu-id="5c52a-117">Zrušení ve spravovaných vláknech</span><span class="sxs-lookup"><span data-stu-id="5c52a-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
