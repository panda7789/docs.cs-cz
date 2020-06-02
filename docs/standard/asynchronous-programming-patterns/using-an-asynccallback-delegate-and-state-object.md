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
ms.openlocfilehash: e52ed550510253aba9401931c0f612211c7d1bf5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276423"
---
# <a name="using-an-asynccallback-delegate-and-state-object"></a>Použití delegáta AsyncCallback a stavového objektu
Použijete-li <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně, můžete použít objekt stavu k předání informací mezi zpětnými voláními a k načtení konečného výsledku. Toto téma ukazuje tento postup rozbalením příkladu v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve <xref:System.Net.Dns> třídě pro načtení informací o systému DNS (Domain Name System) pro uživatelem definované počítače. Tento příklad definuje a používá `HostRequest` třídu k ukládání informací o stavu. Vytvoří se `HostRequest` objekt pro každý název počítače zadaný uživatelem. Tento objekt je předán <xref:System.Net.Dns.BeginGetHostByName%2A> metodě. `ProcessDnsInformation`Metoda je volána pokaždé, když je požadavek dokončen. `HostRequest`Objekt je načten pomocí <xref:System.IAsyncResult.AsyncState%2A> Vlastnosti. `ProcessDnsInformation`Metoda používá `HostRequest` objekt k uložení <xref:System.Net.IPHostEntry> vráceného požadavkem nebo <xref:System.Net.Sockets.SocketException> vyvolaným požadavkem. Po dokončení všech požadavků aplikace provede iteraci `HostRequest` objektů a zobrazí informace DNS nebo <xref:System.Net.Sockets.SocketException> chybovou zprávu.  
  
 [!code-csharp[AsyncDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateWithStateObject.cs#5)]
 [!code-vb[AsyncDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateWithStateObject.vb#5)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
- [Použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)
