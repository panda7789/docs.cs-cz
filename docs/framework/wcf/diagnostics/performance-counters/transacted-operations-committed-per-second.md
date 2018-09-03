---
title: Počet potvrzených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 7318921b-47c4-4c8c-9fdd-41a92061c53f
ms.openlocfilehash: 124eae3b36a731ac50a147782b19c87e3adfa7be
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467471"
---
# <a name="transacted-operations-committed-per-second"></a><span data-ttu-id="12116-102">Počet potvrzených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="12116-102">Transacted Operations Committed Per Second</span></span>
<span data-ttu-id="12116-103">Název čítače: Počet potvrzených zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="12116-103">Counter Name: Transacted Operations Committed Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="12116-104">Popis</span><span class="sxs-lookup"><span data-stu-id="12116-104">Description</span></span>  
 <span data-ttu-id="12116-105">Počet transakční operace, které byly v této službě potvrzen za sekundu.</span><span class="sxs-lookup"><span data-stu-id="12116-105">Number of transactional operations that have been committed in this service in a second.</span></span>  
  
 <span data-ttu-id="12116-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="12116-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="12116-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="12116-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
