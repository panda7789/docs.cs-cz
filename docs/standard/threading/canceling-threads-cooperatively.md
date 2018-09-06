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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43885860"
---
# <a name="canceling-threads-cooperatively"></a>Spolupráce při rušení vláken

Rozhraní .NET Framework před rozhraní .NET Framework 4, k dispozici žádné předdefinované způsob, jak zrušit vlákno kooperativně po jeho spuštění. Nicméně od verze rozhraní .NET Framework 4, můžete použít <xref:System.Threading.CancellationToken?displayProperty=nameWithType> zrušit vlákna, stejně jako můžete využít k zrušit <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty nebo dotazy PLINQ. I když <xref:System.Threading.Thread?displayProperty=nameWithType> třídy nenabízí integrovanou podporu pro tokeny zrušení, můžete předat token procedura vlákna s použitím <xref:System.Threading.Thread> konstruktor, který přijímá <xref:System.Threading.ParameterizedThreadStart> delegovat. Následující příklad demonstruje, jak to udělat.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
