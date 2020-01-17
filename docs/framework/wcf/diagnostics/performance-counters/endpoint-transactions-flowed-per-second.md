---
title: 'Koncový bod: Počet plynoucích transakcí za sekundu'
ms.date: 03/30/2017
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
ms.openlocfilehash: 39458dcb6ac033fd5084b5f2e760e0e26c345da7
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163550"
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="46021-102">Koncový bod: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="46021-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="46021-103">Název čítače: počet toků transakcí za sekundu.</span><span class="sxs-lookup"><span data-stu-id="46021-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="46021-104">Popis</span><span class="sxs-lookup"><span data-stu-id="46021-104">Description</span></span>  
 <span data-ttu-id="46021-105">Počet transakcí, které byly v tomto koncovém bodu převedeny do operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="46021-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="46021-106">Tento čítač se zvyšuje vždy, když se ve zprávě odeslané do koncového bodu nachází ID transakce.</span><span class="sxs-lookup"><span data-stu-id="46021-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="46021-107">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="46021-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="46021-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="46021-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
