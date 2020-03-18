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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73130927"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Použití delegáta AsyncCallback k ukončení asynchronní operace
Aplikace, které mohou dělat jinou práci při čekání na výsledky asynchronní operace by nemělblokovat čekání až do dokončení operace. Pomocí jedné z následujících možností pokračujte v provádění pokynů při čekání na dokončení asynchronní operace:  
  
- Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně. Tento přístup je demonstrován v tomto tématu.  
  
- Pomocí <xref:System.IAsyncResult.IsCompleted%2A> vlastnosti <xref:System.IAsyncResult> vrácené metodou **Begin**_OperationName_ asynchronní operace určete, zda byla operace dokončena. Příklad, který ukazuje tento přístup, naleznete [v tématu dotazování pro stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací DNS (Domain Name System) pro počítače zadané uživatelem. Tento příklad <xref:System.AsyncCallback> vytvoří delegáta, `ProcessDnsInformation` který odkazuje na metodu. Tato metoda je volána jednou pro každý asynchronní požadavek na informace DNS.  
  
 Všimněte si, že hostitel zadaný uživatelem je předán parametru. <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> Příklad, který ukazuje definování a použití složitější objekt stavu, naleznete [v tématu použití AsyncCallback delegate a state Object](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [Volání asynchronních metod pomocí rozhraní IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)
- [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
