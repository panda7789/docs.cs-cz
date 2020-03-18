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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123965"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Dotazování na stav asynchronní operace
Aplikace, které mohou dělat jinou práci při čekání na výsledky asynchronní operace by nemělblokovat čekání až do dokončení operace. Pomocí jedné z následujících možností pokračujte v provádění pokynů při čekání na dokončení asynchronní operace:  
  
- Pomocí <xref:System.IAsyncResult.IsCompleted%2A> vlastnosti <xref:System.IAsyncResult> vrácené metodou **Begin**_OperationName_ asynchronní operace určete, zda byla operace dokončena. Tento přístup se označuje jako dotazování a je demonstrován v tomto tématu.  
  
- Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatném vlákně. Příklad, který ukazuje tento přístup, naleznete [v tématu použití AsyncCallback delegáta ukončit asynchronní operaci](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních <xref:System.Net.Dns> metod ve třídě k načtení informací o systému DNS pro počítač zadaný uživatelem. Tento příklad spustí asynchronní operaci a potom vytiskne tečky (".") v konzole, dokud nebude operace dokončena. Všimněte si, že **null** (**Nothing** v jazyce Visual Basic) je předán pro <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> parametry a, <xref:System.Object> protože tyto argumenty nejsou vyžadovány při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
