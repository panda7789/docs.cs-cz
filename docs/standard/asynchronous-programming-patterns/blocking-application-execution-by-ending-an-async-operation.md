---
title: "Blokování provádění aplikace ukončením asynchronní operace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- blocks, asynchronous operations
- AsyncWaitHandle property
- asynchronous programming, blocking applications
- blocking application execution
ms.assetid: cc5e2834-a65b-4df8-b750-7bdb79997fee
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
dev_langs:
- csharp
- vb
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d9e7a80a9012e85038b72f429e2da569cc43f0bf
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokování provádění aplikace ukončením asynchronní operace
Aplikace, které nelze nadále provádět další činnosti při čekání na výsledky asynchronní operace musí blok, dokud se operace nedokončí. Blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Volání asynchronních operací **End** *OperationName* metoda. Tento přístup je ukázáno v tomto tématu.  
  
-   Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít** *OperationName* metoda. Příklad, který představuje tuto metodu, najdete v části [blokování aplikace provádění pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které používají **End** *OperationName* bude obvykle volání metody blokování až do dokončení asynchronní operaci **začít**  *OperationName* metody provedení veškerou práci, kterou lze provést bez výsledky operace a pak zavolají **End** *OperationName*.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému názvů domény pro počítač zadaného uživatelem. Všimněte si, že `null` (`Nothing` v jazyce Visual Basic) je pro předán <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` a `stateObject` parametry vzhledem k tomu, že tyto argumenty nejsou povinné, při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
