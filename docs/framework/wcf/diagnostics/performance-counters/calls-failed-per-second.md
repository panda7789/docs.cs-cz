---
title: Počet nezdařených volání za sekundu
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: ff9320b0990a0543bbb1da553d040ff5a4b4fed9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797420"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="1b472-102">Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="1b472-102">Calls Failed Per Second</span></span>
<span data-ttu-id="1b472-103">Název čítače: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="1b472-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="1b472-104">Popis</span><span class="sxs-lookup"><span data-stu-id="1b472-104">Description</span></span>  
 <span data-ttu-id="1b472-105">Počet volání s neošetřenými výjimkami v této operaci za sekundu.</span><span class="sxs-lookup"><span data-stu-id="1b472-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="1b472-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="1b472-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="1b472-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="1b472-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="1b472-108">Tento čítač je zvýšena pokaždé, když dojde k neošetřené výjimce v této operaci.</span><span class="sxs-lookup"><span data-stu-id="1b472-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b472-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1b472-109">See also</span></span>

- [<span data-ttu-id="1b472-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="1b472-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
