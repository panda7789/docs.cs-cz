---
title: 'Služba: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: 5189a78e2655707d165f187e06ac9a60d055eac0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773315"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="7bebf-102">Služba: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="7bebf-102">Service: Calls Per Second</span></span>
<span data-ttu-id="7bebf-103">Název čítače: Počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="7bebf-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7bebf-104">Popis</span><span class="sxs-lookup"><span data-stu-id="7bebf-104">Description</span></span>  
 <span data-ttu-id="7bebf-105">Počet volání této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="7bebf-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="7bebf-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="7bebf-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7bebf-107">(N 1 - N 0) / ((D 1 -D 0) / F) čitatel (N) představuje počet operací provedených během posledního intervalu vzorkování, jmenovatel (D) představuje počet taktů vypršel během posledního intervalu vzorkování, kde F je frekvence dílků.</span><span class="sxs-lookup"><span data-stu-id="7bebf-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
