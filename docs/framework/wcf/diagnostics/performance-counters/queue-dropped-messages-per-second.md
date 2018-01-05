---
title: "Počet zpráv vyřazených z fronty za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8512c757f7a18172b267fe7d3469b1a2749818aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="de73a-102">Počet zpráv vyřazených z fronty za sekundu</span><span class="sxs-lookup"><span data-stu-id="de73a-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="de73a-103">Název čítače: Zařadit do fronty ztracených zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="de73a-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="de73a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="de73a-104">Description</span></span>  
 <span data-ttu-id="de73a-105">Počet zpráv, které jsou vynechány podle zařazených do fronty přenosu v této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="de73a-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="de73a-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="de73a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="de73a-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="de73a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
