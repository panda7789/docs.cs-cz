---
title: "Koncový bod: Počet nezdařených volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbe9da4-c8dd-4e27-b630-11611adc7580
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5da436c5e8159ff922c36172490a28e854bbee8b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint-calls-failed-per-second"></a><span data-ttu-id="ee4d3-102">Koncový bod: Počet nezdařených volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="ee4d3-102">Endpoint: Calls Failed Per Second</span></span>
<span data-ttu-id="ee4d3-103">Název čítače: Počet nezdařených volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="ee4d3-103">Counter Name: Calls Failed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ee4d3-104">Popis</span><span class="sxs-lookup"><span data-stu-id="ee4d3-104">Description</span></span>  
 <span data-ttu-id="ee4d3-105">Počet volání, které mají neošetřené výjimky a tento koncový bod přijatých za sekundu.</span><span class="sxs-lookup"><span data-stu-id="ee4d3-105">Number of calls that have unhandled exceptions and are received by this endpoint in a second.</span></span>  
  
 <span data-ttu-id="ee4d3-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="ee4d3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="ee4d3-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="ee4d3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>  
  
 <span data-ttu-id="ee4d3-108">Hodnota tohoto čítače se zvýší pokaždé, když dojde k neošetřené výjimce na tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ee4d3-108">This counter is incremented every time there is an unhandled exception at this endpoint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee4d3-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee4d3-109">See Also</span></span>  
 [<span data-ttu-id="ee4d3-110">Určování a zpracování chyb v kontraktech a službách</span><span class="sxs-lookup"><span data-stu-id="ee4d3-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
