---
title: 'Koncový bod: počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 25e504221097505e622a3ba60f0c7e85ec455f36
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163615"
---
# <a name="endpoint-calls-failed-per-second"></a>Koncový bod: počet nezdařených volání za sekundu
Název čítače: počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání s neošetřenými výjimkami, které jsou přijímány tímto koncovým bodem za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Tento čítač se zvýší pokaždé, když se v tomto koncovém bodu nachází Neošetřená výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)
