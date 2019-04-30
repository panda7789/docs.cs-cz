---
title: Volání asynchronních metod pomocí rozhraní IAsyncResult
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01001d68b4bee42453fcb84725507b0cf61184a1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61870185"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>Volání asynchronních metod pomocí rozhraní IAsyncResult
Typy v rozhraní .NET Framework a knihovny tříd třetích stran můžou poskytovat metody, které umožňují aplikace má pokračovat provedením při provádění asynchronní operace ve vláknech než hlavního vlákna aplikace. Následující části popisují a poskytnout příklady kódu, které ukazují různé způsoby, jak můžete volat asynchronní metody, které používají <xref:System.IAsyncResult> vzoru návrhu.  
  
- [Blokování provádění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- [Blokování provádění aplikací pomocí vlastnosti AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Použití delegáta AsyncCallback k ukončení asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také:

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
