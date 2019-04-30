---
title: Počet nezdařených relací spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916120"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a>Počet nezdařených relací spolehlivého zasílání zpráv za sekundu
Název čítače: Počet nezdařených relací spolehlivého zasílání zpráv za sekundu.  
  
## <a name="description"></a>Popis  
 Počet relací spolehlivého zasílání zpráv, které jsou s chybou v této službě za sekundu.  
  
 Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
