---
title: "Spolupráce při rušení vláken"
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
helpviewer_keywords: threads, cancellation
ms.assetid: d2d6d5fd-e263-4fa0-847b-2fc3e0d82337
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 334cbcf8b4a888dbac5962c0fd668673e15e0e29
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="canceling-threads-cooperatively"></a>Spolupráce při rušení vláken
Před verzí [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], rozhraní .NET Framework poskytuje integrované způsob, jak zrušit vlákno spolupráce při po jeho spuštění. Ale v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít zrušení tokenů zrušení vláken, stejně, jako je můžete zrušit <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty nebo dotazy PLINQ. I když <xref:System.Threading.Thread?displayProperty=nameWithType> třída nenabízí integrovanou podporu pro zrušení tokenů, můžete předat token vlákna proceduře pomocí <xref:System.Threading.Thread> konstruktor, který přebírá <xref:System.Threading.ParameterizedThreadStart> delegovat. Následující příklad demonstruje, jak to udělat.  
  
 [!code-csharp[Cancellation#14](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/CooperativeThreads.cs#14)]
 [!code-vb[Cancellation#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/CooperativeThreads.vb#14)]  
  
## <a name="see-also"></a>Viz také  
 [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
