---
title: Počet nezdařených volání za sekundu
ms.date: 03/30/2017
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
ms.openlocfilehash: e7c0b53f4c2b1a7e87a5791b44e452ec9146c459
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321126"
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="b58f4-102">Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="b58f4-102">Calls Failed Per Second</span></span>
<span data-ttu-id="b58f4-103">Název čítače: počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="b58f4-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="b58f4-104">Popis</span><span class="sxs-lookup"><span data-stu-id="b58f4-104">Description</span></span>  
 <span data-ttu-id="b58f4-105">Počet volání s neošetřenými výjimkami v této operaci za sekundu</span><span class="sxs-lookup"><span data-stu-id="b58f4-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="b58f4-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="b58f4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b58f4-107">(N 1-N 0)/((D 1-D 0)/F)</span><span class="sxs-lookup"><span data-stu-id="b58f4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="b58f4-108">Tento čítač se zvýší pokaždé, když v této operaci dojde k neošetřené výjimce.</span><span class="sxs-lookup"><span data-stu-id="b58f4-108">This counter is incremented every time there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58f4-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b58f4-109">See also</span></span>

- [<span data-ttu-id="b58f4-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="b58f4-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../specifying-and-handling-faults-in-contracts-and-services.md)
