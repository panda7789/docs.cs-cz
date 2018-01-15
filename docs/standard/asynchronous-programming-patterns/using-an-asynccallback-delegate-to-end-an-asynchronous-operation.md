---
title: "Použití delegáta AsyncCallback k ukončení asynchronní operace"
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
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d71e78ecd5bf365d0a1f3efb8c8e15d4a1de6dc7
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2018
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Použití delegáta AsyncCallback k ukončení asynchronní operace
Aplikace, které můžete provádět další činnosti při čekání na výsledky asynchronní operace by neměly blokovat, počkejte, až se dokončí. Pokud chcete pokračovat v provádění pokyny při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatné vlákno. Tento přístup je ukázáno v tomto tématu.  
  
-   Použití <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít *** OperationName* metoda k určení, zda bude dokončena operace. Příklad, který představuje tuto metodu, najdete v části [dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému DNS (Domain Name) pro počítače zadaného uživatelem. Tento příklad vytvoří <xref:System.AsyncCallback> delegáta, který odkazuje `ProcessDnsInformation` metoda. Tato metoda je volána jednou pro každý asynchronní požadavek informace DNS.  
  
 Všimněte si, že je předán hostitele zadán uživatel <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametr. Příklad, který ukazuje definování a používání složitější objekt stavu, naleznete v části [použití delegáta AsyncCallback a objekt stavu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 [Volání asynchronních metod pomocí rozhraní IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
 [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
