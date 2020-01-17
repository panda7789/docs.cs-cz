---
title: 'Koncový bod: počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
ms.openlocfilehash: 25e504221097505e622a3ba60f0c7e85ec455f36
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163615"
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="ec12e-102">Koncový bod: počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="ec12e-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="ec12e-103">Název čítače: počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="ec12e-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ec12e-104">Popis</span><span class="sxs-lookup"><span data-stu-id="ec12e-104">Description</span></span>  
 <span data-ttu-id="ec12e-105">Počet volání s neošetřenými výjimkami, které jsou přijímány tímto koncovým bodem za sekundu.</span><span class="sxs-lookup"><span data-stu-id="ec12e-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="ec12e-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="ec12e-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ec12e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="ec12e-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ec12e-108">Tento čítač se zvýší pokaždé, když se v tomto koncovém bodu nachází Neošetřená výjimka.</span><span class="sxs-lookup"><span data-stu-id="ec12e-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec12e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ec12e-109">See also</span></span>

- [<span data-ttu-id="ec12e-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="ec12e-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
