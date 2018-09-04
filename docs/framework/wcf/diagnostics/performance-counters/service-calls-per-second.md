---
title: 'Služba: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499884"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="83a91-102">Služba: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="83a91-102">Service: Calls Per Second</span></span>
<span data-ttu-id="83a91-103">Název čítače: Počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="83a91-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="83a91-104">Popis</span><span class="sxs-lookup"><span data-stu-id="83a91-104">Description</span></span>  
 <span data-ttu-id="83a91-105">Počet volání této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="83a91-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="83a91-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="83a91-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="83a91-107">(N 1 - N 0) / ((D 1 -D 0) / F) čitatel (N) představuje počet operací provedených během posledního intervalu vzorkování, jmenovatel (D) představuje počet taktů vypršel během posledního intervalu vzorkování, kde F je frekvence dílků.</span><span class="sxs-lookup"><span data-stu-id="83a91-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
