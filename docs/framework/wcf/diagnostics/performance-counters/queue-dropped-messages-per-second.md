---
title: Počet zpráv vyřazených z fronty za sekundu
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916159"
---
# <a name="queue-dropped-messages-per-second"></a>Počet zpráv vyřazených z fronty za sekundu
Název čítače: Počet zrušených zpráv fronty za sekundu.  
  
## <a name="description"></a>Popis  
 Počet zpráv, které jsou zařazené do fronty přenosu v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
