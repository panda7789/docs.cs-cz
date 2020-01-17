---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: e165348a71101b21fa66bd4907c43335b1e476e4
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163979"
---
# <a name="service-calls-failed-per-second"></a>Služba: Počet nezdařených volání za sekundu
Název čítače: počet nezdařených volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání s neošetřenými výjimkami, které služba obdrží za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)  
  
 Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.  
  
 Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.  
  
 Tento čítač se zvýší pokaždé, když v této službě dojde k neošetřené výjimce.  
  
## <a name="see-also"></a>Viz také:

- [Určování a zpracování chyb v kontraktech a službách](../../specifying-and-handling-faults-in-contracts-and-services.md)
