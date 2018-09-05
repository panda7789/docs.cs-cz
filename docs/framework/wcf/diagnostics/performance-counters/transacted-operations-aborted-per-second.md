---
title: Počet zrušených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500556"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="015f3-102">Počet zrušených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="015f3-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="015f3-103">Název čítače: Stažení operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="015f3-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="015f3-104">Popis</span><span class="sxs-lookup"><span data-stu-id="015f3-104">Description</span></span>  
 <span data-ttu-id="015f3-105">Počet transakční operace, které byla pravděpodobně přerušena v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="015f3-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="015f3-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="015f3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="015f3-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="015f3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
