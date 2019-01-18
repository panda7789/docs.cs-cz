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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
ms.openlocfilehash: 854528670bbddbc2dc318bf4a5ecd12368a5e8d1
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54361973"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokování provádění aplikace ukončením asynchronní operace
Aplikace, které nemůže pokračovat v další práci při čekání na výsledcích asynchronní operaci musí blokovat až do dokončení operace. Blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Volání asynchronních operací **End**_OperationName_ metody. Tento přístup je ukázáno v tomto tématu.  
  
-   Použití <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operace **začít**_OperationName_ metody. Příklad, který ukazuje tento přístup, najdete v části [blokování aplikace spuštění pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které používají **End**_OperationName_ obvykle bude volat metodu blokovat, dokud se asynchronní operace nebude dokončena **začít**  _OperationName_ metody provést žádnou práci, kterou můžete provést bez výsledku operace a následně zavolat **End**_OperationName_.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třídy načíst informace o systému názvů domény pro počítače zadané uživatelem. Všimněte si, že `null` (`Nothing` v jazyce Visual Basic) je předán <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` a `stateObject` parametry vzhledem k tomu, že tyto argumenty nejsou vyžadovány, při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
