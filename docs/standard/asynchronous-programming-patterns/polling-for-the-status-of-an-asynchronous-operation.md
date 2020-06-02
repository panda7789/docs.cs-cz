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
ms.openlocfilehash: f10b4ae5617edc8cf8a38a6cbac999e10a935dc2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291380"
---
# <a name="polling-for-the-status-of-an-asynchronous-operation"></a>Dotazování na stav asynchronní operace
Aplikace, které mohou provádět jiné operace při čekání na výsledky asynchronní operace, by neměly zablokovat čekání na dokončení operace. Pomocí jedné z následujících možností můžete pokračovat v provádění pokynů při čekání na dokončení asynchronní operace:  
  
- <xref:System.IAsyncResult.IsCompleted%2A> <xref:System.IAsyncResult> K určení, zda byla operace dokončena, použijte vlastnost vrácenou metodou **Begin**_OperationName_ asynchronní operace. Tento přístup se označuje jako cyklické dotazování a je znázorněno v tomto tématu.  
  
- Použijte <xref:System.AsyncCallback> delegáta pro zpracování výsledků asynchronní operace v samostatném vlákně. Příklad, který demonstruje tento přístup, najdete v tématu [použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje použití asynchronních metod ve <xref:System.Net.Dns> třídě pro načtení informací o systému názvů domén pro uživatelem zadaný počítač. Tento příklad spustí asynchronní operaci a poté vytiskne tečky (".") v konzole nástroje, dokud není operace dokončena. Všimněte si, že **hodnota null** (**Nothing** v Visual Basic) je předána pro <xref:System.Net.Dns.BeginGetHostByName%2A> <xref:System.AsyncCallback> parametry a, <xref:System.Object> protože při použití tohoto přístupu nejsou tyto argumenty požadovány.  
  
 [!code-csharp[AsyncDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/Async_Poll.cs#3)]
 [!code-vb[AsyncDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/Async_Poll.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
