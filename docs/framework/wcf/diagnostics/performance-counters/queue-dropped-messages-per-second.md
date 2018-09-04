---
title: Počet zpráv vyřazených z fronty za sekundu
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: f15b2db08ac4486377189a1533b653260d79024a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528120"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="437c0-102">Počet zpráv vyřazených z fronty za sekundu</span><span class="sxs-lookup"><span data-stu-id="437c0-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="437c0-103">Název čítače: Zařadí do fronty zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="437c0-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="437c0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="437c0-104">Description</span></span>  
 <span data-ttu-id="437c0-105">Počet zpráv, které jsou zařazené do fronty přenosu v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="437c0-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="437c0-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="437c0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="437c0-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="437c0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
