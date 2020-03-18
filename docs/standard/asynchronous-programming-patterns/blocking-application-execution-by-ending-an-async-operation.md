---
title: Blokování provádění aplikace ukončením asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
dev_langs:
- csharp
- vb
ms.openlocfilehash: aed3b18c154d4b7a4390b28fb1f14536690f6b3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121331"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokování provádění aplikace ukončením asynchronní operace
Aplikace, které nemohou pokračovat v jiné práci při čekání na výsledky asynchronní operace, musí blokovat, dokud nebude operace dokončena. Pomocí jedné z následujících možností zablokujte hlavní vlákno aplikace při čekání na dokončení asynchronní operace:  
  
- Volání asynchronní operace **End**_OperationName_ metoda. Tento přístup je demonstrován v tomto tématu.  
  
- Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost vrácené <xref:System.IAsyncResult> metodou **Begin**_OperationName_ asynchronní operace. Příklad, který ukazuje tento přístup, naleznete [v tématu blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které používají **end**_OperationName_ metoda blokovat, dokud asynchronní operace je dokončena obvykle volat **Begin**_OperationName_ metoda, provádět všechny práce, které lze provést bez výsledků operace a potom volání **End**_OperationName_.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací o systému DNS pro počítač zadaný uživatelem. Všimněte `null` `Nothing` si, že (v <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` jazyce Visual Basic) je předán pro parametry a, `stateObject` protože tyto argumenty nejsou vyžadovány při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
