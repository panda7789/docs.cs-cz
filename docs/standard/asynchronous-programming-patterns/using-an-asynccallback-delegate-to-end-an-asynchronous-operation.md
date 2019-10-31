---
title: Použití delegáta AsyncCallback k ukončení asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: c3cac2db57a24bf6a0f5640e4ad8101686e6c3e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130927"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Použití delegáta AsyncCallback k ukončení asynchronní operace
Aplikace, které mohou provádět jiné operace při čekání na výsledky asynchronní operace, by neměly zablokovat čekání na dokončení operace. Pomocí jedné z následujících možností můžete pokračovat v provádění pokynů při čekání na dokončení asynchronní operace:  
  
- Použijte delegáta <xref:System.AsyncCallback> pro zpracování výsledků asynchronní operace v samostatném vlákně. Tento přístup je znázorněný v tomto tématu.  
  
- K určení, zda byla operace dokončena, použijte vlastnost <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> vrácenou metodou **Begin**_OperationName_ asynchronní operace. Příklad, který demonstruje tento přístup, najdete v tématu [cyklické dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě <xref:System.Net.Dns> k načtení informací DNS (Domain Name System) pro uživatelem definované počítače. Tento příklad vytvoří delegáta <xref:System.AsyncCallback>, který odkazuje na metodu `ProcessDnsInformation`. Tato metoda se volá jednou pro každý asynchronní požadavek na informace DNS.  
  
 Všimněte si, že uživatel zadaný uživatelem je předán parametru <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object>. Příklad, který ukazuje definování a použití složitějšího objektu stavu, naleznete v tématu [použití delegáta AsyncCallback a objektu State](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Volání asynchronních metod pomocí rozhraní IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
