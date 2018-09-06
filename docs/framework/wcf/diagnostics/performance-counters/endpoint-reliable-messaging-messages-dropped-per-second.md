---
title: 'Koncový bod: Počet zrušených spolehlivých zpráv za sekundu'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737578"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="85f85-102">Koncový bod: Počet zrušených spolehlivých zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="85f85-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="85f85-103">Název čítače: Relací spolehlivého zasílání zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="85f85-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="85f85-104">Popis</span><span class="sxs-lookup"><span data-stu-id="85f85-104">Description</span></span>  
 <span data-ttu-id="85f85-105">Celkový počet spolehlivého zasílání zpráv, které byly vynechány v tomto koncovém bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="85f85-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="85f85-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="85f85-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="85f85-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="85f85-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
