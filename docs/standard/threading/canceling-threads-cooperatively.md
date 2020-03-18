---
title: Spolupráce při rušení vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
ms.openlocfilehash: 1d1433ecf39974bf9e68fe07b9d0818ac16fb544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138127"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="da45b-102">Spolupráce při rušení vláken</span><span class="sxs-lookup"><span data-stu-id="da45b-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="da45b-103">Před rozhraním .NET Framework 4 rozhraní .NET Framework neposkytl žádný předdefinovaný způsob, jak po spuštění kooperativně zrušit vlákno.</span><span class="sxs-lookup"><span data-stu-id="da45b-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="da45b-104">Nicméně počínaje rozhraním .NET Framework 4 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> můžete použít ke zrušení podprocesů, stejně jako je můžete použít ke zrušení <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objektů nebo plinq dotazů.</span><span class="sxs-lookup"><span data-stu-id="da45b-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="da45b-105">Přestože <xref:System.Threading.Thread?displayProperty=nameWithType> třída nenabízí integrovanou podporu pro tokeny zrušení, můžete předat token <xref:System.Threading.Thread> do procedury <xref:System.Threading.ParameterizedThreadStart> podprocesu pomocí konstruktoru, který přebírá delegáta.</span><span class="sxs-lookup"><span data-stu-id="da45b-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="da45b-106">Následující příklad demonstruje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="da45b-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="da45b-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="da45b-107">See also</span></span>

- [<span data-ttu-id="da45b-108">Použití vláken a zřetězení</span><span class="sxs-lookup"><span data-stu-id="da45b-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
