---
title: Počet poškozených zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420686"
---
# <a name="queued-poison-messages-per-second"></a>Počet poškozených zpráv za sekundu
Název čítače: Nezpracovatelných zpráv za sekundu zařazených do fronty.  
  
## <a name="description"></a>Popis  
 Počet zpráv, které jsou označeny zařazených do fronty přenosu v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
