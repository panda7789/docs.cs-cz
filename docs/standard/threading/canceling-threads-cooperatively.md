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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd32deb9c8719a12b76aaea8ec91a17471cf18f9
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221490"
---
# <a name="canceling-threads-cooperatively"></a><span data-ttu-id="17b3c-102">Spolupráce při rušení vláken</span><span class="sxs-lookup"><span data-stu-id="17b3c-102">Canceling threads cooperatively</span></span>

<span data-ttu-id="17b3c-103">Rozhraní .NET Framework před rozhraní .NET Framework 4, k dispozici žádné předdefinované způsob, jak zrušit vlákno kooperativně po jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="17b3c-103">Prior to the .NET Framework 4, the .NET Framework provided no built-in way to cancel a thread cooperatively after it was started.</span></span> <span data-ttu-id="17b3c-104">Nicméně od verze rozhraní .NET Framework 4, můžete použít <xref:System.Threading.CancellationToken?displayProperty=nameWithType> zrušit vlákna, stejně jako můžete využít k zrušit <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty nebo dotazy PLINQ.</span><span class="sxs-lookup"><span data-stu-id="17b3c-104">However, starting with the .NET Framework 4, you can use a <xref:System.Threading.CancellationToken?displayProperty=nameWithType> to cancel threads, just as you can use them to cancel <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objects or PLINQ queries.</span></span> <span data-ttu-id="17b3c-105">I když <xref:System.Threading.Thread?displayProperty=nameWithType> třídy nenabízí integrovanou podporu pro tokeny zrušení, můžete předat token procedura vlákna s použitím <xref:System.Threading.Thread> konstruktor, který přijímá <xref:System.Threading.ParameterizedThreadStart> delegovat.</span><span class="sxs-lookup"><span data-stu-id="17b3c-105">Although the <xref:System.Threading.Thread?displayProperty=nameWithType> class does not offer built-in support for cancellation tokens, you can pass a token to a thread procedure by using the <xref:System.Threading.Thread> constructor that takes a <xref:System.Threading.ParameterizedThreadStart> delegate.</span></span> <span data-ttu-id="17b3c-106">Následující příklad demonstruje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="17b3c-106">The following example demonstrates how to do this.</span></span>  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="17b3c-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17b3c-107">See also</span></span>

- [<span data-ttu-id="17b3c-108">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="17b3c-108">Using Threads and Threading</span></span>](using-threads-and-threading.md)
