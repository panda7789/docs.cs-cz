---
title: 'Koncový bod: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: c0273fc90ad5702663862612f52f03c42f410b8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint-calls-failed-per-second"></a>Koncový bod: Počet nezdařených volání za sekundu
Název čítače: Počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které mají neošetřené výjimky a tento koncový bod přijatých za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)  
  
 Hodnota tohoto čítače se zvýší pokaždé, když dojde k neošetřené výjimce na tento koncový bod.  
  
## <a name="see-also"></a>Viz také  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
