---
title: Počet plynoucích transakcí za sekundu
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: a71095b9fdd16d7e220be8a0aeb0a746bb50527e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472915"
---
# <a name="transactions-flowed-per-second"></a>Počet plynoucích transakcí za sekundu
Název čítače: Počet plynoucích transakcí za sekundu  
  
## <a name="description"></a>Popis  
 Počet transakcí plynoucích s touto operací za sekundu. Tento čítač se zvýší, když je součástí zprávy, která je odeslána operaci ID transakce.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)
