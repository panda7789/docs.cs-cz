---
title: 'Služba: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: ec72eb49-2942-4811-91df-d6e5dad81fd8
ms.openlocfilehash: 1151117c8537d4a8eaa4de60d14e314b55ce82d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="service-transactions-flowed-per-second"></a>Služba: Počet plynoucích transakcí za sekundu
Název čítače: Plynoucích transakcí za sekundu.  
  
## <a name="description"></a>Popis  
 Počet transakcí předávány operace v rámci této služby za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)
