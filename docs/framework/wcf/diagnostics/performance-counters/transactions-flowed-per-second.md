---
title: Počet plynoucích transakcí za sekundu
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927189"
---
# <a name="transactions-flowed-per-second"></a>Počet plynoucích transakcí za sekundu
Název čítače:  Počet plynoucích transakcí za sekundu  
  
## <a name="description"></a>Popis  
 Počet transakcí, které byly převedeny do této operace za sekundu. Tento čítač se zvýší pokaždé, když je k dispozici v zpráva odeslaná do operace ID transakce.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
