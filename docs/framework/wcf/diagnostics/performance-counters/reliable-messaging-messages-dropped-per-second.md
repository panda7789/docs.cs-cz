---
title: Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916029"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu
Název čítače: Relace spolehlivého zasílání zpráv za sekundu.  
  
## <a name="description"></a>Popis  
 Celkový počet spolehlivého zasílání zpráv, které byly vynechány v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
