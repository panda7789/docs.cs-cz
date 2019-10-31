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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121331"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokování provádění aplikace ukončením asynchronní operace
Aplikace, které nemohou pokračovat v provádění jiné práce při čekání na výsledky asynchronní operace musí blokovat až do dokončení operace. Použijte jednu z následujících možností k blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace:  
  
- Zavolejte metodu **End**_operace_ pro asynchronní operace. Tento přístup je znázorněný v tomto tématu.  
  
- Použijte vlastnost <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> vrácená metodou **Begin**_OperationName_ asynchronní operace. Příklad, který demonstruje tento přístup, naleznete v tématu [blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které používají metodu **End**_OperationName_ k blokování, dokud není dokončena asynchronní operace, obvykle volají metodu **Begin**_OperationName_ , provádějí všechny práce, které lze provést bez výsledků operaci a potom zavolejte **End**_NázevOperace_.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě <xref:System.Net.Dns> k načtení informací o systému názvů domén pro uživatelem zadaný počítač. Všimněte si, že `null` (`Nothing` v Visual Basic) se předává pro parametry <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` a `stateObject`, protože při použití tohoto přístupu se tyto argumenty nevyžadují.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
