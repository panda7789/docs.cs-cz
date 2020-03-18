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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73094607"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Použití delegáta AsyncCallback a stavového objektu
Při použití <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně, můžete použít objekt stavu předat informace mezi zpětná volání a načíst konečný výsledek. Toto téma ukazuje, že praxe rozbalením příklad u [použití AsyncCallback delegát a ukončit asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací DNS (Domain Name System) pro počítače zadané uživatelem. Tento příklad definuje a `HostRequest` používá třídu k ukládání informací o stavu. Objekt `HostRequest` bude vytvořen pro každý název počítače zadaný uživatelem. Tento objekt je <xref:System.Net.Dns.BeginGetHostByName%2A> předán metodě. Metoda `ProcessDnsInformation` je volána při každém dokončení požadavku. Objekt `HostRequest` je načten pomocí <xref:System.IAsyncResult.AsyncState%2A> vlastnosti. Metoda `ProcessDnsInformation` používá `HostRequest` objekt k <xref:System.Net.IPHostEntry> uložení vrácené požadavek nebo <xref:System.Net.Sockets.SocketException> vyvolána požadavek. Po dokončení všech požadavků aplikace iterates `HostRequest` přes objekty a <xref:System.Net.Sockets.SocketException> zobrazí informace DNS nebo chybová zpráva.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
