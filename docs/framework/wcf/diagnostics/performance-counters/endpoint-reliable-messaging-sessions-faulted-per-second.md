---
title: 'Koncový bod: Počet nezdařených relací spolehlivého zasílání zpráv za sekundu'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 198acbeff6b8a54dcc6e4ae6966fea996da4b745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472768"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a>Koncový bod: Počet nezdařených relací spolehlivého zasílání zpráv za sekundu
Název čítače: Relací spolehlivého zasílání zpráv s chybou za sekundu.  
  
## <a name="description"></a>Popis  
 Počet relací spolehlivého zasílání zpráv, které se nezdařily na tento koncový bod za sekundu.  
  
 Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.  
  
 (NE 1 - N 0) / ((D 1 - D 0) / F)
