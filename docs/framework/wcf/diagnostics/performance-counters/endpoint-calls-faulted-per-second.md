---
title: 'Koncový bod: Počet volání s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: 9840fc0a-0e4d-4638-96fd-40e3ab9e4667
ms.openlocfilehash: ead4b074748307f30d16557c3359f730880595da
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163537"
---
# <a name="endpoint-calls-faulted-per-second"></a>Koncový bod: Počet volání s chybou za sekundu
Název čítače: počet volání s chybou za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, která vrátily chyby do tohoto koncového bodu za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 V aplikacích Windows Communication Foundation (WCF) metody služeb sdělují informace o chybě zpracování pomocí zpráv o chybách protokolu SOAP. Chyby protokolu SOAP jsou typy zpráv, které jsou zahrnuty v metadatech pro operaci služby. proto je možné vytvořit kontrakt selhání, který mohou klienti použít, aby jejich spuštění bylo robustnější nebo interaktivní. Vzhledem k tomu, že chyby protokolu SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce interoperabilní.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)
