---
title: "Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle"
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
- blocks, asynchronous operations
- ending asynchronous operations
- asynchronous programming, ending operations
- asynchronous programming, blocking applications
- stopping asynchronous operations
- blocking application execution
ms.assetid: 3e32daf2-8161-4e8f-addd-9fd9ff101b03
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 380080c0aa05bc5b94c9ec5fe471f2f255562cd2
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2018
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle
Aplikace, které nelze nadále provádět další činnosti při čekání na výsledky asynchronní operace musí blok, dokud se operace nedokončí. Blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít *** OperationName* metoda. Tento přístup je ukázáno v tomto tématu.  
  
-   Volání asynchronní operaci **End *** OperationName* metoda. Příklad, který představuje tuto metodu, najdete v části [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikace, které používají jeden nebo více <xref:System.Threading.WaitHandle> objekty, které chcete blokovat až do dokončení asynchronní operace obvykle zavolá **začít *** OperationName* metoda, provádět veškerou práci, kterou lze provést bez výsledky operace a potom blok až do dokončení asynchronní operace. Aplikace můžete blokovat v rámci jedné operace mezi voláním <xref:System.Threading.WaitHandle.WaitOne%2A> metod pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Blokování při čekání na sadu na dokončení asynchronních operací, uložení přidruženého <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a volání jednoho <xref:System.Threading.WaitHandle.WaitAll%2A> metody. Blokování při čekání na některého z sadu na dokončení asynchronních operací, uložení přidruženého <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a volání jednoho <xref:System.Threading.WaitHandle.WaitAny%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS načíst informace o systému názvů domény pro počítač zadaného uživatelem. Příklad ukazuje blokování pomocí <xref:System.Threading.WaitHandle> přidružené asynchronní operace. Všimněte si, že `null` (`Nothing` v jazyce Visual Basic) je pro předán <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` a `stateObject` parametry protože tyto nejsou požadovány při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
