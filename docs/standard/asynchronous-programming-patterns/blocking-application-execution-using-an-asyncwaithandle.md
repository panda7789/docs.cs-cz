---
title: Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
ms.openlocfilehash: 16b5a297c13cd9096548ed489e4994b72a48da67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121430"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle
Aplikace, které nemohou pokračovat v jiné práci při čekání na výsledky asynchronní operace, musí blokovat, dokud nebude operace dokončena. Pomocí jedné z následujících možností zablokujte hlavní vlákno aplikace při čekání na dokončení asynchronní operace:  
  
- Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost vrácené <xref:System.IAsyncResult> metodou **Begin**_OperationName_ asynchronní operace. Tento přístup je demonstrován v tomto tématu.  
  
- Volání asynchronní operace **End**_OperationName_ metoda. Příklad, který ukazuje tento přístup, naleznete [v tématu blokování spuštění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikace, které používají <xref:System.Threading.WaitHandle> jeden nebo více objektů k zablokování, dokud není dokončena asynchronní operace, obvykle volají metodu **Begin**_OperationName,_ provádějí jakoukoli práci, kterou lze provést bez výsledků operace, a poté blokují, dokud nebude dokončena asynchronní operace. Aplikace může blokovat na jednu operaci <xref:System.Threading.WaitHandle.WaitOne%2A> voláním <xref:System.IAsyncResult.AsyncWaitHandle%2A>jedné z metod pomocí . Chcete-li blokovat při čekání na sadu asynchronních operací <xref:System.IAsyncResult.AsyncWaitHandle%2A> k dokončení, uložte <xref:System.Threading.WaitHandle.WaitAll%2A> přidružené objekty v poli a volání jedné z metod. Chcete-li blokovat při čekání na některou ze sady asynchronních <xref:System.IAsyncResult.AsyncWaitHandle%2A> operací k dokončení, uložte přidružené objekty v poli a volání jedné z <xref:System.Threading.WaitHandle.WaitAny%2A> metod.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS k načtení informací o systému DNS pro počítač zadaný uživatelem. Příklad ukazuje blokování pomocí <xref:System.Threading.WaitHandle> přidružené asynchronní operace. Všimněte `null` `Nothing` si, že (v <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` jazyce Visual Basic) je předán pro parametry a, `stateObject` protože tyto nejsou vyžadovány při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
