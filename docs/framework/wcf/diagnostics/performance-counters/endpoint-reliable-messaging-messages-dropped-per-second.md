---
title: 'Koncový bod: Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: 8f935bee06d175ce454bd7f58a1afbbe9ab505ad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797199"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="c8535-102">Koncový bod: Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="c8535-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="c8535-103">Název čítače: Relace spolehlivého zasílání zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="c8535-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c8535-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c8535-104">Description</span></span>  
 <span data-ttu-id="c8535-105">Celkový počet spolehlivého zasílání zpráv, které byly vynechány v tomto koncovém bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="c8535-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="c8535-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="c8535-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c8535-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="c8535-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
