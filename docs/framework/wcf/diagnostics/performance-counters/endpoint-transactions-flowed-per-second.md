---
title: "Koncový bod: Počet plynoucích transakcí za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f370ff1-a913-450b-bccb-c279ad165b3d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 58d1bec0110d669258e8f003cb1e882207133a5d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-transactions-flowed-per-second"></a><span data-ttu-id="a089c-102">Koncový bod: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="a089c-102">Endpoint: Transactions Flowed Per Second</span></span>
<span data-ttu-id="a089c-103">Název čítače: Plynoucích transakcí za sekundu.</span><span class="sxs-lookup"><span data-stu-id="a089c-103">Counter Name: Transactions Flowed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a089c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a089c-104">Description</span></span>  
 <span data-ttu-id="a089c-105">Počet transakcí plynoucích do operací na tento koncový bod za sekundu.</span><span class="sxs-lookup"><span data-stu-id="a089c-105">Number of transactions flowed to operations at this endpoint in a second.</span></span> <span data-ttu-id="a089c-106">Tento čítač se zvýší, když ID transakce je součástí zprávy odeslané ke koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="a089c-106">This counter is incremented any time a transaction ID is present in a message sent to the endpoint.</span></span>  
  
 <span data-ttu-id="a089c-107">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="a089c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a089c-108">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="a089c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
