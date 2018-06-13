---
title: Počet zpráv vyřazených z fronty za sekundu
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 47835086a4ee920e814d9dd6c1e41b9cdc33efec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471466"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="62852-102">Počet zpráv vyřazených z fronty za sekundu</span><span class="sxs-lookup"><span data-stu-id="62852-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="62852-103">Název čítače: Zařadit do fronty ztracených zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="62852-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62852-104">Popis</span><span class="sxs-lookup"><span data-stu-id="62852-104">Description</span></span>  
 <span data-ttu-id="62852-105">Počet zpráv, které jsou vynechány podle zařazených do fronty přenosu v této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="62852-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="62852-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="62852-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="62852-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="62852-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
