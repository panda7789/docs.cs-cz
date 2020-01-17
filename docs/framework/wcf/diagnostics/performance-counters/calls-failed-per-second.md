---
title: Počet nezdařených volání za sekundu
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: 110ee5c264094f80d5c7c6542c3e388e758e1665
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163160"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="04021-102">Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="04021-102">Calls Failed Per Second</span></span>
<span data-ttu-id="04021-103">Název čítače: počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="04021-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="04021-104">Popis</span><span class="sxs-lookup"><span data-stu-id="04021-104">Description</span></span>  
 <span data-ttu-id="04021-105">Počet volání s neošetřenými výjimkami v této operaci za sekundu</span><span class="sxs-lookup"><span data-stu-id="04021-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="04021-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="04021-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="04021-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="04021-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="04021-108">Tento čítač se zvýší pokaždé, když v této operaci dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="04021-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04021-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04021-109">See also</span></span>

- [<span data-ttu-id="04021-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="04021-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
