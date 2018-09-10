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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46b7839a6bd0086a8ec82e416cdf7aed05707390
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213498"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Použití delegáta AsyncCallback a stavového objektu
Při použití <xref:System.AsyncCallback> delegovat ke zpracování výsledků asynchronních operací v samostatném vlákně, můžete použít stav objektu k předávání informací mezi zpětných dotazů a k načítání konečný výsledek. Toto téma popisuje tento postup tak, že rozbalíte v příkladu v [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třídy se načíst informace o systému DNS (Domain Name) pro počítače zadané uživatelem. Tento příklad definuje a používá `HostRequest` třídu pro ukládání informací o stavu. A `HostRequest` objekt se vytvoří pro každý název počítače zadané uživatelem. Tento objekt je předán <xref:System.Net.Dns.BeginGetHostByName%2A> metody. `ProcessDnsInformation` Metoda je volána pokaždé, když se dokončí požadavek. `HostRequest` Objektu jsou načítány s použitím <xref:System.IAsyncResult.AsyncState%2A> vlastnost. `ProcessDnsInformation` Metoda používá `HostRequest` objekt pro uložení <xref:System.Net.IPHostEntry> vráceným žádostí nebo <xref:System.Net.Sockets.SocketException> vyvolána v požadavku. Po dokončení všech žádostí aplikace iteruje `HostRequest` objekty a zobrazí informace o DNS nebo <xref:System.Net.Sockets.SocketException> chybovou zprávu.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [Použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
