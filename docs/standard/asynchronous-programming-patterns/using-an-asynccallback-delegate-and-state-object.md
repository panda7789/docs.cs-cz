---
title: Použití delegáta AsyncCallback a stavového objektu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, delegates
- AsyncCallback delegate, samples
- asynchronous programming, state objects
- IAsyncResult interface, samples
ms.assetid: e3e5475d-c5e9-43f0-928e-d18df8ca1f1d
ms.openlocfilehash: c7bd0a7606b5f93289cf39d33794457265e7e453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094607"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Použití delegáta AsyncCallback a stavového objektu
Použijete-li delegáta <xref:System.AsyncCallback> ke zpracování výsledků asynchronní operace v samostatném vlákně, můžete použít stavový objekt k předání informací mezi zpětnými voláními a k načtení konečného výsledku. Toto téma ukazuje tento postup rozbalením příkladu v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě <xref:System.Net.Dns> k načtení informací DNS (Domain Name System) pro uživatelem definované počítače. Tento příklad definuje a používá třídu `HostRequest` k uložení informací o stavu. Vytvoří se objekt `HostRequest` pro každý název počítače zadaný uživatelem. Tento objekt je předán metodě <xref:System.Net.Dns.BeginGetHostByName%2A>. Metoda `ProcessDnsInformation` je volána pokaždé, když je požadavek dokončen. Objekt `HostRequest` je načten pomocí vlastnosti <xref:System.IAsyncResult.AsyncState%2A>. Metoda `ProcessDnsInformation` používá objekt `HostRequest` k uložení <xref:System.Net.IPHostEntry> vráceného požadavkem nebo <xref:System.Net.Sockets.SocketException> vyvolaným požadavkem. Po dokončení všech požadavků aplikace provede iteraci objektů `HostRequest` a zobrazí informace o DNS nebo <xref:System.Net.Sockets.SocketException> chybovou zprávu.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
