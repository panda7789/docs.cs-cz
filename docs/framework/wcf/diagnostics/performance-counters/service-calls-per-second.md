---
title: 'Služba: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499884"
---
# <a name="service-calls-per-second"></a>Služba: Počet volání za sekundu
Název čítače: Počet volání za sekundu.  
  
## <a name="description"></a>Popis  
 Počet volání této služby za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0) / ((D 1 -D 0) / F) čitatel (N) představuje počet operací provedených během posledního intervalu vzorkování, jmenovatel (D) představuje počet taktů vypršel během posledního intervalu vzorkování, kde F je frekvence dílků.
