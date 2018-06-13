---
title: 'Koncový bod: Počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: 186d59d2f0255f0f964130659a2053fc8f440dd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474503"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="62d3d-102">Koncový bod: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="62d3d-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="62d3d-103">Název čítače: Počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="62d3d-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="62d3d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="62d3d-104">Description</span></span>  
 <span data-ttu-id="62d3d-105">Počet volání k tomuto koncovému bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="62d3d-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="62d3d-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="62d3d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="62d3d-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="62d3d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
