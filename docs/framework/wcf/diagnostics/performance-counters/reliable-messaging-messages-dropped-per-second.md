---
title: Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 946e0408b8b6602bba7824b45e4d6cb91cdaa4eb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163953"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a>Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu
Název čítače: počet vynechaných relací spolehlivého zasílání zpráv za sekundu.  
  
## <a name="description"></a>Popis  
 Celkový počet zpráv spolehlivého zasílání zpráv, které byly v této službě vyřazeny za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
