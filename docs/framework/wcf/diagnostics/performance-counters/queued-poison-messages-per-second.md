---
title: Počet poškozených zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: d4c921b105dfd1c1a364d2c86f54ab920078dd4a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916146"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="9f8fc-102">Počet poškozených zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="9f8fc-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="9f8fc-103">Název čítače: Počet Nezpracovatelných zpráv za sekundu zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="9f8fc-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9f8fc-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9f8fc-104">Description</span></span>  
 <span data-ttu-id="9f8fc-105">Počet zpráv, které jsou označeny zařazených do fronty přenosu v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="9f8fc-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="9f8fc-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="9f8fc-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9f8fc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9f8fc-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
