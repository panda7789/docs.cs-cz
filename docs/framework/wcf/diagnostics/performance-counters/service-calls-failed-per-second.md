---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 5431144a4618b146a10dfaa3bbdaae34c519319e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315782"
---
# <a name="service-calls-failed-per-second"></a>Služba: Počet nezdařených volání za sekundu
Název čítače: počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání s neošetřenými výjimkami, které služba obdrží za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1-N 0)/((D 1-D 0)/F)  
  
 Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.  
  
 Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.  
  
 Tento čítač se zvýší pokaždé, když v této službě dojde k neošetřené výjimce.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)
