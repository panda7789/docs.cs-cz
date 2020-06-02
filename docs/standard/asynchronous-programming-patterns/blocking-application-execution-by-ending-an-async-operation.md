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
ms.openlocfilehash: 74976176acc0fbb948c514358b7bd323cc20c134
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289951"
---
# <a name="blocking-application-execution-by-ending-an-async-operation"></a>Blokování provádění aplikace ukončením asynchronní operace
Aplikace, které nemohou pokračovat v provádění jiné práce při čekání na výsledky asynchronní operace musí blokovat až do dokončení operace. Použijte jednu z následujících možností k blokování hlavního vlákna aplikace při čekání na dokončení asynchronní operace:  
  
- Zavolejte metodu **End**_operace_ pro asynchronní operace. Tento přístup je znázorněný v tomto tématu.  
  
- Použijte <xref:System.IAsyncResult.AsyncWaitHandle%2A> vlastnost <xref:System.IAsyncResult> vrácenou metodou **Begin**_OperationName_ asynchronní operace. Příklad, který demonstruje tento přístup, naleznete v tématu [blokování spuštění aplikace pomocí AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
 Aplikace, které používají metodu **End**_OperationName_ k blokování, dokud není dokončena asynchronní operace, obvykle volají metodu **Begin**_OperationName_ , provádějí všechny práce, které lze provést bez výsledků operace, a poté zavolejte funkci **End**_NázevOperace_.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve <xref:System.Net.Dns> třídě pro načtení informací o systému názvů domén pro uživatelem zadaný počítač. Všimněte si, že `null` ( `Nothing` v Visual Basic) je předán pro <xref:System.Net.Dns.BeginGetHostByName%2A> `requestCallback` parametry a, `stateObject` protože při použití tohoto přístupu nejsou tyto argumenty požadovány.  
  
 [!code-csharp[AsyncDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_EndBlock.cs#1)]
 [!code-vb[AsyncDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_EndBlock.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
