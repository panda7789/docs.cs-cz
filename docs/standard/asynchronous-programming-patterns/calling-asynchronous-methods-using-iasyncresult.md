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
ms.openlocfilehash: 2a9ce8bc2d2edd09ef79c060b9bb173d4d054d02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121316"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>Volání asynchronních metod pomocí rozhraní IAsyncResult
Typy v rozhraní .NET Framework a knihovnách tříd třetích stran mohou poskytovat metody, které umožňují aplikaci pokračovat v provádění při provádění asynchronních operací v jiných vláknech než v hlavním vlákně aplikace. Následující části popisují a poskytují příklady kódu, které ukazují různé způsoby, <xref:System.IAsyncResult> jak můžete volat asynchronní metody, které používají návrhový vzor.  
  
- [Blokování spuštění aplikace ukončením asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-by-ending-an-async-operation.md).  
  
- [Blokování spuštění aplikace pomocí AsyncWaitHandle](../../../docs/standard/asynchronous-programming-patterns/blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Dotazování na stav asynchronní operace](../../../docs/standard/asynchronous-programming-patterns/polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Použití asyncCallback delegáta ukončit asynchronní operaci](../../../docs/standard/asynchronous-programming-patterns/using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
