---
title: 'Koncový bod: počet relací spolehlivého zasílání zpráv s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 26fd8236af6516716f7cf9c7c06f669473bdfc3a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163186"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Koncový bod: počet relací spolehlivého zasílání zpráv s chybou za sekundu
Název čítače: v relacích spolehlivého zasílání zpráv došlo k chybě za sekundu.  
  
## <a name="description"></a>Popis  
 Počet relací spolehlivého zasílání zpráv, u kterých došlo k chybě v tomto koncovém bodu za sekundu.  
  
 Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
