---
title: 'Koncový bod: počet volání za sekundu'
ms.date: 03/30/2017
ms.assetid: ca0fc06d-d68f-4236-bd5f-c7ff6214acdd
ms.openlocfilehash: d639d881bcedd336c7bbabd28ec385f60ff54d43
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163784"
---
# <a name="endpoint-calls-per-second"></a><span data-ttu-id="e61df-102">Koncový bod: počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="e61df-102">Endpoint: Calls Per Second</span></span>
<span data-ttu-id="e61df-103">Název čítače: počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="e61df-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e61df-104">Popis</span><span class="sxs-lookup"><span data-stu-id="e61df-104">Description</span></span>  
 <span data-ttu-id="e61df-105">Počet volání tohoto koncového bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="e61df-105">Number of calls to this endpoint in a second.</span></span>  
  
 <span data-ttu-id="e61df-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="e61df-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="e61df-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="e61df-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
