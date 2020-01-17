---
title: 'Služba: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: be5d77169a71d6f44205a1150da5239eceff7d9c
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163901"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="33578-102">Služba: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="33578-102">Service: Calls Per Second</span></span>
<span data-ttu-id="33578-103">Název čítače: počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="33578-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="33578-104">Popis</span><span class="sxs-lookup"><span data-stu-id="33578-104">Description</span></span>  
 <span data-ttu-id="33578-105">Počet volání této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="33578-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="33578-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="33578-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="33578-107">(N 1-N 0)/((D 1-D 0)/F) kde čitatel (N) představuje počet operací provedených během posledního ukázkového intervalu, jmenovatel (D) představuje počet taktů uplynulých během posledního ukázkového intervalu a F je frekvence impulsů.</span><span class="sxs-lookup"><span data-stu-id="33578-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
