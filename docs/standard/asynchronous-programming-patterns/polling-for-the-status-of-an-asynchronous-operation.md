---
title: Dotazování na stav asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
ms.openlocfilehash: ff9cefc73adfe1ece1bf7545c75ccb6cc618e89f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123965"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Dotazování na stav asynchronní operace
Aplikace, které mohou provádět jiné operace při čekání na výsledky asynchronní operace, by neměly zablokovat čekání na dokončení operace. Pomocí jedné z následujících možností můžete pokračovat v provádění pokynů při čekání na dokončení asynchronní operace:  
  
- K určení, zda byla operace dokončena, použijte vlastnost <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> vrácenou metodou **Begin**_OperationName_ asynchronní operace. Tento přístup se označuje jako cyklické dotazování a je znázorněno v tomto tématu.  
  
- Použijte delegáta <xref:System.AsyncCallback> pro zpracování výsledků asynchronní operace v samostatném vlákně. Příklad, který demonstruje tento přístup, najdete v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve třídě <xref:System.Net.Dns> k načtení informací o systému názvů domén pro uživatelem zadaný počítač. Tento příklad spustí asynchronní operaci a poté vytiskne tečky (".") v konzole nástroje, dokud není operace dokončena. Všimněte si, že **hodnota null** (**Nothing** v Visual Basic) se předává pro <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.AsyncCallback> a parametry <xref:System.Object>, protože tyto argumenty se při použití tohoto přístupu nevyžadují.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
