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
ms.openlocfilehash: 88ca1b5bfbb8bfbdfef01dea8af07c5d56784c5c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289912"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>Volání asynchronních metod pomocí rozhraní IAsyncResult
Typy v .NET Framework a knihovny tříd třetích stran mohou poskytovat metody, které umožní aplikaci pokračovat v provádění při provádění asynchronních operací v jiných vláknech než v rámci hlavního vlákna aplikace. Následující části popisují a poskytují příklady kódu, které ukazují různé způsoby, jak můžete volat asynchronní metody, které používají <xref:System.IAsyncResult> návrhový vzor.  
  
- [Blokování provádění aplikace ukončením asynchronní operace](blocking-application-execution-by-ending-an-async-operation.md).  
  
- [Blokování spuštění aplikace pomocí AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [Cyklické dotazování na stav asynchronní operace](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [Použití delegáta AsyncCallback k ukončení asynchronní operace](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>Viz také

- [Asynchronní vzor založený na událostech (EAP)](event-based-asynchronous-pattern-eap.md)
- [Přehled asynchronních vzorů založených na událostech](event-based-asynchronous-pattern-overview.md)
