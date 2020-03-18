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
# <a name="canceling-threads-cooperatively"></a>Spolupráce při rušení vláken

Před rozhraním .NET Framework 4 rozhraní .NET Framework neposkytl žádný předdefinovaný způsob, jak po spuštění kooperativně zrušit vlákno. Nicméně počínaje rozhraním .NET Framework 4 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> můžete použít ke zrušení podprocesů, stejně jako je můžete použít ke zrušení <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objektů nebo plinq dotazů. Přestože <xref:System.Threading.Thread?displayProperty=nameWithType> třída nenabízí integrovanou podporu pro tokeny zrušení, můžete předat token <xref:System.Threading.Thread> do procedury <xref:System.Threading.ParameterizedThreadStart> podprocesu pomocí konstruktoru, který přebírá delegáta. Následující příklad demonstruje, jak to udělat.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Viz také

- [Použití vláken a zřetězení](using-threads-and-threading.md)
