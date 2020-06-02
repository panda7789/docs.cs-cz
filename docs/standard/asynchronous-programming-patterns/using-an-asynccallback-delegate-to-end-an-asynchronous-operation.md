---
title: Použití delegáta AsyncCallback k ukončení asynchronní operace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: 8766e64c52688e820d0eb6a259e39926555d97bd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276346"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Použití delegáta AsyncCallback k ukončení asynchronní operace
Aplikace, které mohou provádět jiné operace při čekání na výsledky asynchronní operace, by neměly zablokovat čekání na dokončení operace. Pomocí jedné z následujících možností můžete pokračovat v provádění pokynů při čekání na dokončení asynchronní operace:  
  
- Použijte <xref:System.AsyncCallback> delegáta pro zpracování výsledků asynchronní operace v samostatném vlákně. Tento přístup je znázorněný v tomto tématu.  
  
- <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> K určení, zda byla operace dokončena, použijte vlastnost vrácenou metodou **Begin**_OperationName_ asynchronní operace. Příklad, který demonstruje tento přístup, najdete v tématu [cyklické dotazování na stav asynchronní operace](polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve <xref:System.Net.Dns> třídě pro načtení informací o systému DNS (Domain Name System) pro uživatelem definované počítače. Tento příklad vytvoří <xref:System.AsyncCallback> delegáta, který odkazuje na `ProcessDnsInformation` metodu. Tato metoda se volá jednou pro každý asynchronní požadavek na informace DNS.  
  
 Všimněte si, že zadaný uživatel je předán <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru. Příklad, který ukazuje definování a použití složitějšího objektu stavu, naleznete v tématu [použití delegáta AsyncCallback a objektu State](using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
- [Volání asynchronních metod pomocí rozhraní IAsyncResult](calling-asynchronous-methods-using-iasyncresult.md)
- [Použití delegáta AsyncCallback a stavového objektu](using-an-asynccallback-delegate-and-state-object.md)
