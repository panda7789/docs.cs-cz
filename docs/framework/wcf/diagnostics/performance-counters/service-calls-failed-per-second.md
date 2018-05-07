---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 6af8f79d1fe163967a5c6e8220697aa11bee66c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="service-calls-failed-per-second"></a>Služba: Počet nezdařených volání za sekundu
Název čítače: Počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání, které mají neošetřené výjimky a tato služba přijímá za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)  
  
 Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.  
  
 Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.  
  
 Hodnota tohoto čítače se zvýší pokaždé, když dojde k neošetřené výjimce v rámci této služby.  
  
## <a name="see-also"></a>Viz také  
 [Určování a zpracování chyb v kontraktech a službách](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
