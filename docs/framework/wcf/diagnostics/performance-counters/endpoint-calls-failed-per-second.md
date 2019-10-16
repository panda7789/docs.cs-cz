---
title: 'Koncový bod: počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 9634f8a170bb2fae2f15c3f00dcabb95d512c74e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321463"
---
# <a name="endpoint-calls-failed-per-second"></a>Koncový bod: počet nezdařených volání za sekundu
Název čítače: počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání s neošetřenými výjimkami, které jsou přijímány tímto koncovým bodem za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Tento čítač se zvýší pokaždé, když se v tomto koncovém bodu nachází Neošetřená výjimka.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)
