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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138127"
---
# <a name="canceling-threads-cooperatively"></a>Spolupráce při rušení vláken

Před .NET Framework 4 neposkytovala .NET Framework žádný vestavěný způsob, jak v družstvu po svém spuštění zrušit vlákno. Počínaje .NET Framework 4 ale můžete použít <xref:System.Threading.CancellationToken?displayProperty=nameWithType> k zrušení vlákna, stejně jako můžete použít k zrušení objektů <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo PLINQ dotazů. I když třída <xref:System.Threading.Thread?displayProperty=nameWithType> nenabízí integrovanou podporu pro tokeny zrušení, můžete předat token proceduře vlákna pomocí <xref:System.Threading.Thread> konstruktoru, který přebírá <xref:System.Threading.ParameterizedThreadStart> delegát. Následující příklad demonstruje, jak to udělat.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Viz také:

- [Použití vláken a dělení na vlákna](using-threads-and-threading.md)
