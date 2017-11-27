---
title: "Použití delegáta AsyncCallback a stavového objektu"
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
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e8793a78289e9b58407038f41cc9d403ff9f9940
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Použití delegáta AsyncCallback a stavového objektu
Když použijete <xref:System.AsyncCallback> delegovat ke zpracování výsledků asynchronní operace v samostatné vlákno, můžete použít objekt stavu k předávání informací mezi zpětná volání a k načítání konečný výsledek. Toto téma ukazuje, že postup rozšířením v příkladu v [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému DNS (Domain Name) pro počítače zadaného uživatelem. Tento příklad definuje a používá `HostRequest` třídu pro ukládání informací o stavu. A `HostRequest` objekt se vytvoří pro každý název počítače zadaného uživatelem. Tento objekt je předán <xref:System.Net.Dns.BeginGetHostByName%2A> metoda. `ProcessDnsInformation` Metoda je volána při každém dokončení požadavku. `HostRequest` Objekt je načíst pomocí <xref:System.IAsyncResult.AsyncState%2A> vlastnost. `ProcessDnsInformation` Metoda používá `HostRequest` objekt pro uložení <xref:System.Net.IPHostEntry> vrácených požadavkem nebo <xref:System.Net.Sockets.SocketException> vyvolané žádosti. Po dokončení všech požadavků aplikace iteruje nad `HostRequest` objekty a zobrazí informace o DNS nebo <xref:System.Net.Sockets.SocketException> chybová zpráva.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
