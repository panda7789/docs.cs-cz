---
title: 'Koncový bod: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: ff3d76025bbae0759dba005adbd62609701c5a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33471279"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="8d777-102">Koncový bod: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="8d777-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="8d777-103">Název čítače: Plynoucích transakcí za sekundu.</span><span class="sxs-lookup"><span data-stu-id="8d777-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8d777-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8d777-104">Description</span></span>  
 <span data-ttu-id="8d777-105">Počet transakcí plynoucích do operací na tento koncový bod za sekundu.</span><span class="sxs-lookup"><span data-stu-id="8d777-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="8d777-106">Tento čítač se zvýší, když ID transakce je součástí zprávy odeslané ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="8d777-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="8d777-107">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="8d777-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8d777-108">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="8d777-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
