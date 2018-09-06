---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 9cd649788e1304c68caa1bbf4b5fd27e6fc9d508
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861813"
---
# <a name="service-calls-failed-per-second"></a>Služba: Počet nezdařených volání za sekundu
Název čítače: Počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které mají neošetřené výjimky a tato služba přijatých za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)  
  
 Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.  
  
 Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.  
  
 Tento čítač se zvyšuje vždy, když dojde k neošetřené výjimce v této službě.  
  
## <a name="see-also"></a>Viz také  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
