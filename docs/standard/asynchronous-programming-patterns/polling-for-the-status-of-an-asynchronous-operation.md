---
title: "Dotazování na stav asynchronní operace"
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
- asynchronous programming, status polling
- polling asynchronous operation status
- status information [.NET Framework], asynchronous operations
ms.assetid: b541af31-dacb-4e20-8847-1b1ff7c35363
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 094aefbe20f3e366fc15c2cc0f920a6fcd189074
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Dotazování na stav asynchronní operace
Aplikace, které můžete provádět další činnosti při čekání na výsledky asynchronní operace by neměly blokovat, počkejte, až se dokončí. Pokud chcete pokračovat v provádění pokyny při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Použití <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operaci **začít** *OperationName* metoda k určení, zda bude dokončena operace. Tento postup se označuje jako cyklického dotazování a je ukázáno v tomto tématu.  
  
-   Použijte <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronní operace v samostatné vlákno. Příklad, který představuje tuto metodu, najdete v části [použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třída načíst informace o systému názvů domény pro počítač zadaného uživatelem. Tento příkaz spustí asynchronní operaci a potom zobrazí tečky (".") v konzole, dokud se nedokončí operaci. Všimněte si, že **null** (**nic** v jazyce Visual Basic) byla předána pro <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> a <xref:System.Object> parametry vzhledem k tomu, že tyto argumenty nejsou povinné, při použití tohoto přístupu.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
