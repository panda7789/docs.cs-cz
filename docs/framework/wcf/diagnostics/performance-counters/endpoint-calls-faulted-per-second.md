---
title: 'Koncový bod: Počet volání s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: 3b5c881c4ce7772e197bfc1a5603636b0975143c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517653"
---
# <a name="endpoint-calls-faulted-per-second"></a>Koncový bod: Počet volání s chybou za sekundu
Název čítače: Počet volání s chybou za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které se mají vrátit chyby k tomuto koncovému bodu za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 V aplikacích Windows Communication Foundation (WCF) komunikují metod služby informace o chybě zpracování pomocí chybové zprávy protokolu SOAP. Typy zpráv, které jsou zahrnuty v metadatech pro operaci služby a proto vytvořit selhání kontrakt, který můžou klienti použít k jejich spuštění zkontrolujte robustní nebo interaktivní jsou chyby SOAP. Protože chyb SOAP jsou vyjádřeny klientům v podobě XML, jsou vysoce interoperabilní.  
  
## <a name="see-also"></a>Viz také:
- [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
