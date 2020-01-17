---
title: Počet volání s chybou za sekundu
ms.date: 03/30/2017
ms.assetid: 81c88073-8e32-4520-a71a-2c56b71ee515
ms.openlocfilehash: 37fd47a3e4ca474338a4a6ae1117c2626acb546f
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163147"
---
# <a name="calls-faulted-per-second"></a>Počet volání s chybou za sekundu
Název čítače: počet volání s chybou za sekundu  
  
## <a name="description"></a>Popis  
 Počet volání, která této operaci vrátila chybu, za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 V aplikacích Windows Communication Foundation (WCF) metody služeb sdělují informace o chybě zpracování pomocí zpráv o chybách protokolu SOAP. Chyby protokolu SOAP jsou typy zpráv, které jsou zahrnuty v metadatech pro operaci služby. proto je možné vytvořit kontrakt selhání, který mohou klienti použít, aby jejich spuštění bylo robustnější nebo interaktivní. Vzhledem k tomu, že chyby protokolu SOAP jsou vyjádřeny klientům ve formátu XML, jsou vysoce interoperabilní.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)
