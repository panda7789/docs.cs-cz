---
title: 'Koncový bod: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: a70df63f6fd268abdd2e1799d1aa38afb41e2811
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486919"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="e20f6-102">Koncový bod: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="e20f6-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="e20f6-103">Název čítače: Počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="e20f6-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e20f6-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e20f6-104">Description</span></span>  
 <span data-ttu-id="e20f6-105">Počet volání tohoto koncového bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="e20f6-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e20f6-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="e20f6-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e20f6-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="e20f6-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
