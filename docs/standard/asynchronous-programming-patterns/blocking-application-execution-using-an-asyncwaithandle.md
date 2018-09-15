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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 054af36987d60c8aeb752c9c711f1cce19733efc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45624467"
---
# <a name="blocking-application-execution-using-an-asyncwaithandle"></a>Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle
Aplikace, které nemůže pokračovat v další práci při čekání na výsledcích asynchronní operaci musí blokovat až do dokončení operace. Blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operace **začít *** OperationName* metody. Tento přístup je ukázáno v tomto tématu.  
  
-   Volání asynchronní operace **End *** OperationName* metody. Příklad, který ukazuje tento přístup, najdete v části [blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
 Aplikace, které používají jeden nebo více <xref:System.Threading.WaitHandle> objekty zablokována až do dokončení asynchronní operace se bude obvykle volat **začít *** OperationName* metody provádět každé dílo, který se dá udělat bez výsledky operace a potom bloku až do dokončení asynchronní operace. Aplikace může blokovat v rámci jedné operace vyvoláním některé z <xref:System.Threading.WaitHandle.WaitOne%2A> metod pomocí <xref:System.IAsyncResult.AsyncWaitHandle%2A>. Blokovat čekání na sadu na dokončení asynchronních operací, ukládání přidruženého <xref:System.IAsyncResult.AsyncWaitHandle%2A> objektů v poli a volání jeden <xref:System.Threading.WaitHandle.WaitAll%2A> metody. Blokovat čekání na některou z sadu na dokončení asynchronních operací, ukládání přidruženého <xref:System.IAsyncResult.AsyncWaitHandle%2A> objektů v poli a volání jeden <xref:System.Threading.WaitHandle.WaitAny%2A> metody.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě DNS pro načtení informací Domain Name System pro počítače zadané uživatelem. Tento příklad ukazuje blokování používání <xref:System.Threading.WaitHandle> přidružené k asynchronní operaci. Všimněte si, že `null` (`Nothing` v jazyce Visual Basic) je předán <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` a `stateObject` parametry vzhledem k tomu, že se nejedná vyžaduje při tomto postupu.  
  
 [!code-csharp[AsyncDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlockWait.cs#2)]
 [!code-vb[AsyncDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlockWait.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
