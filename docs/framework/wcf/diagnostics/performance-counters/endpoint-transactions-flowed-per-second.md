---
title: 'Koncový bod: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264356"
---
# <a name="endpoint-transactions-flowed-per-second"></a>Koncový bod: Počet plynoucích transakcí za sekundu
Název čítače: Plynoucí transakce za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakcí, které byly převedeny do operací v tomto koncovém bodu za sekundu. Hodnota tohoto čítače se zvýší pokaždé, když ID transakce je k dispozici v zpráva odeslaná do koncového bodu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 - D 0) / F)
