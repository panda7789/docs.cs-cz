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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 856273c9592aa32feb3e8cc66c850cb34ad0812f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079133"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a>Použití delegáta AsyncCallback k ukončení asynchronní operace
Aplikace, které můžete provádět další operace při čekání na výsledcích asynchronní operace by neměly blokovat čekání, až do dokončení operace. Má pokračovat provedením pokyny při čekání na dokončení asynchronní operace, použijte jednu z následujících možností:  
  
-   Použití <xref:System.AsyncCallback> delegáta ke zpracování výsledků asynchronních operací v samostatném vlákně. Tento přístup je ukázáno v tomto tématu.  
  
-   Použití <xref:System.IAsyncResult.IsCompleted%2A> vlastnost <xref:System.IAsyncResult> vrácený asynchronní operace **začít *** OperationName* metodou ke zjištění, zda operace byla dokončena. Příklad, který ukazuje tento přístup, najdete v části [dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod v <xref:System.Net.Dns> třídy se načíst informace o systému DNS (Domain Name) pro počítače zadané uživatelem. Tento příklad vytvoří <xref:System.AsyncCallback> delegát, který odkazuje `ProcessDnsInformation` metody. Tato metoda se volá jednou pro každou asynchronní žádost o informace DNS.  
  
 Všimněte si, že je předán uživatelem zadaného hostitele <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.Object> parametru. Příklad, který znázorňuje definování a použití složitější stav objektu, najdete v části [použití delegáta AsyncCallback a objekt stavu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md).  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
- [Volání asynchronních metod pomocí rozhraní IAsyncResult](../../../docs/standard/asynchronous-programming-patterns/calling-asynchronous-methods-using-iasyncresult.md)  
- [Použití delegáta AsyncCallback a stavového objektu](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-and-state-object.md)
