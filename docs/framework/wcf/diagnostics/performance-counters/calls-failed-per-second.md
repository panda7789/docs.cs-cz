---
title: "Počet nezdařených volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4ef3773-f650-4876-99cf-4d0c02aa03d4
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91f9520750ddd8f35728ae6c5afc2390b7aa8274
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="calls-failed-per-second"></a><span data-ttu-id="c7eb3-102">Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="c7eb3-102">Calls Failed Per Second</span></span>
<span data-ttu-id="c7eb3-103">Název čítače: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="c7eb3-103">Counter Name: Calls Failed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="c7eb3-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c7eb3-104">Description</span></span>  
 <span data-ttu-id="c7eb3-105">Počet volání s neošetřenými výjimkami v této operaci za sekundu.</span><span class="sxs-lookup"><span data-stu-id="c7eb3-105">Number of calls with unhandled exceptions in this operation in a second.</span></span>  
  
 <span data-ttu-id="c7eb3-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="c7eb3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c7eb3-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="c7eb3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="c7eb3-108">Hodnota čítače je zvýšena při dojde k neošetřené výjimce v této operaci.</span><span class="sxs-lookup"><span data-stu-id="c7eb3-108">This counter is incremented everytime there is an unhandled exception in this operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7eb3-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7eb3-109">See Also</span></span>  
 [<span data-ttu-id="c7eb3-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="c7eb3-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
