---
title: 'Koncový bod: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44175014"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Koncový bod: Počet plynoucích transakcí za sekundu
Název čítače: Plynoucí transakce za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakcí, které byly převedeny do operací v tomto koncovém bodu za sekundu. Hodnota tohoto čítače se zvýší pokaždé, když ID transakce je k dispozici v zpráva odeslaná do koncového bodu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
