---
title: Počet nejistých zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076427"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="28917-102">Počet nejistých zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="28917-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="28917-103">Název čítače: Počet nejistých zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="28917-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="28917-104">Popis</span><span class="sxs-lookup"><span data-stu-id="28917-104">Description</span></span>  
 <span data-ttu-id="28917-105">Počet transakční operace s nejistým nejisté v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="28917-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="28917-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="28917-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="28917-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="28917-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
