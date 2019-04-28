---
title: Počet nejistých zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: f7365c4e5f03711129916c8c6964f7e25e9b553e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766334"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="9461a-102">Počet nejistých zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="9461a-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="9461a-103">Název čítače: Za sekundu v nejisté provedené operace.</span><span class="sxs-lookup"><span data-stu-id="9461a-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9461a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="9461a-104">Description</span></span>  
 <span data-ttu-id="9461a-105">Počet transakční operace s nejistým nejisté v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="9461a-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="9461a-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="9461a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="9461a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="9461a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
