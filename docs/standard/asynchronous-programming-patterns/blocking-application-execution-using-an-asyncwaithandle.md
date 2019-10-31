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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121430"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle
Aplikace, které nemohou pokračovat v provádění jiné práce při čekání na výsledky asynchronní operace musí blokovat až do dokončení operace. Použijte jednu z následujících možností k blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace:  
  
- Použijte vlastnost <xref:System.IAsyncResult.AsyncWaitHandle%2A> <xref:System.IAsyncResult> vrácená metodou **Begin**_OperationName_ asynchronní operace. Tento přístup je znázorněný v tomto tématu.  
  
- Zavolejte metodu **End**_OperationName_ asynchronní operace. Příklad, který demonstruje tento přístup, naleznete v tématu [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikace, které používají jeden nebo více <xref:System.Threading.WaitHandle> objektů k blokování, dokud není dokončena asynchronní operace, obvykle volají metodu **Begin**_OperationName_ , provádějí všechny práce, které lze provést bez výsledků operace, a pak zablokují až do dokončení asynchronních operací. Aplikace může zablokovat jednu operaci voláním jedné z <xref:System.Threading.WaitHandle.WaitOne%2A> metod pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Chcete-li blokovat při čekání na dokončení sady asynchronních operací, uložte přidružené <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty v poli a zavolejte jednu z <xref:System.Threading.WaitHandle.WaitAll%2A> metod. Chcete-li zablokovat čekání na dokončení některé ze sady asynchronních operací, uložte přidružené <xref:System.IAsyncResult.AsyncWaitHandle%2A> objekty do pole a zavolejte jednu z <xref:System.Threading.WaitHandle.WaitAny%2A> metod.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS k načtení informací o systému názvů domén pro uživatelem zadaný počítač. Příklad ukazuje blokování pomocí <xref:System.Threading.WaitHandle> přidruženého k asynchronní operaci. Všimněte si, že `null` (`Nothing` v Visual Basic) se předává pro parametry <xref:System.Net.Dns.BeginGetHostByName%2A>`requestCallback` a `stateObject`, protože při použití tohoto přístupu se nevyžadují.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
