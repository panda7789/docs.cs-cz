---
title: 'Koncový bod: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 79f50b6706facd040ec2d325c676f210d5327bf8
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44175014"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="dd280-102">Koncový bod: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="dd280-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="dd280-103">Název čítače: Plynoucí transakce za sekundu.</span><span class="sxs-lookup"><span data-stu-id="dd280-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dd280-104">Popis</span><span class="sxs-lookup"><span data-stu-id="dd280-104">Description</span></span>  
 <span data-ttu-id="dd280-105">Počet transakcí, které byly převedeny do operací v tomto koncovém bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="dd280-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="dd280-106">Hodnota tohoto čítače se zvýší pokaždé, když ID transakce je k dispozici v zpráva odeslaná do koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="dd280-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="dd280-107">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="dd280-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="dd280-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="dd280-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
