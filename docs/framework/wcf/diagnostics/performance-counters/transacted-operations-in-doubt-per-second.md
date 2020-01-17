---
title: Počet nejistých zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7e6b0716-c107-42e5-a21d-31d988e7a691
ms.openlocfilehash: bc978f5b45352fa9fcce5aee5a616c9f86f56aeb
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163836"
---
# <a name="transacted-operations-in-doubt-per-second"></a><span data-ttu-id="b3ee4-102">Počet nejistých zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="b3ee4-102">Transacted Operations In Doubt Per Second</span></span>
<span data-ttu-id="b3ee4-103">Název čítače: počet nejistých zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-103">Counter Name: Transacted Operations In Doubt Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b3ee4-104">Popis</span><span class="sxs-lookup"><span data-stu-id="b3ee4-104">Description</span></span>  
 <span data-ttu-id="b3ee4-105">Počet transakčních operací s nejistým výsledkem v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-105">Number of transactional operations with an in-doubt outcome in this service in a second.</span></span>  
  
 <span data-ttu-id="b3ee4-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="b3ee4-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b3ee4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="b3ee4-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
