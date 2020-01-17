---
title: Počet zpráv vyřazených z fronty za sekundu
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 6ec762d7e5dd7daf63b5df76e1ffb48957538538
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164031"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="77cf0-102">Počet zpráv vyřazených z fronty za sekundu</span><span class="sxs-lookup"><span data-stu-id="77cf0-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="77cf0-103">Název čítače: vyřazené zprávy zařazené do fronty za sekundu.</span><span class="sxs-lookup"><span data-stu-id="77cf0-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="77cf0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="77cf0-104">Description</span></span>  
 <span data-ttu-id="77cf0-105">Počet zpráv, které jsou v této službě zahozeny přenosem ve frontě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="77cf0-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="77cf0-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="77cf0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="77cf0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="77cf0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
