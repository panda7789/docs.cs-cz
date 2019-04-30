---
title: 'Služba: Počet volání s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: 94247356-2b29-4b50-b639-91ca8c1cf3a9
ms.openlocfilehash: 595b623d70bad82ea39ab3ef93fb5fd499268ff2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915704"
---
# <a name="service-calls-faulted-per-second"></a>Služba: Počet volání s chybou za sekundu
Název čítače: Počet volání s chybou za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které se mají vrátit chyby k této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 V aplikacích Windows Communication Foundation (WCF) komunikují metod služby informace o chybě zpracování pomocí chybové zprávy protokolu SOAP. Typy zpráv, které jsou zahrnuty v metadatech pro operaci služby a proto vytvořit selhání kontrakt, který můžou klienti použít k jejich spuštění zkontrolujte robustní nebo interaktivní jsou chyby SOAP. Protože chyb SOAP jsou vyjádřeny klientům v podobě XML, jsou vysoce interoperabilní.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
