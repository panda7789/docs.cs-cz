---
title: 'Služba: Počet nezdařených volání za sekundu'
ms.date: 03/30/2017
ms.assetid: 5a2c7939-107d-4f0c-b43c-e02e079e8a9d
ms.openlocfilehash: 6af8f79d1fe163967a5c6e8220697aa11bee66c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473824"
---
# <a name="service-calls-failed-per-second"></a><span data-ttu-id="bb3eb-102">Služba: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="bb3eb-102">Service: Calls Failed Per Second</span></span>
<span data-ttu-id="bb3eb-103">Název čítače: Počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="bb3eb-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="bb3eb-104">Popis</span><span class="sxs-lookup"><span data-stu-id="bb3eb-104">Description</span></span>  
 <span data-ttu-id="bb3eb-105">Počet volání, které mají neošetřené výjimky a tato služba přijímá za sekundu.</span><span class="sxs-lookup"><span data-stu-id="bb3eb-105">Number of calls that have unhandled exceptions, and are received by this service in a second.</span></span>  
  
 <span data-ttu-id="bb3eb-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="bb3eb-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="bb3eb-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="bb3eb-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="bb3eb-108">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="bb3eb-108">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="bb3eb-109">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="bb3eb-109">In managed code, exceptions are thrown when error conditions occur.</span></span>  
  
 <span data-ttu-id="bb3eb-110">Hodnota tohoto čítače se zvýší pokaždé, když dojde k neošetřené výjimce v rámci této služby.</span><span class="sxs-lookup"><span data-stu-id="bb3eb-110">This counter is incremented every time there is an unhandled exception in this service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3eb-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb3eb-111">See Also</span></span>  
 [<span data-ttu-id="bb3eb-112">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="bb3eb-112">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
