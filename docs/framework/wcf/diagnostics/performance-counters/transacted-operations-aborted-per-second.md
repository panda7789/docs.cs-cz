---
title: Počet zrušených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: 6369fea6def5ebb6b62274caed31d5fb63b3b0e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61998189"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="244b8-102">Počet zrušených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="244b8-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="244b8-103">Název čítače: Počet zrušených zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="244b8-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="244b8-104">Popis</span><span class="sxs-lookup"><span data-stu-id="244b8-104">Description</span></span>  
 <span data-ttu-id="244b8-105">Počet transakční operace, které byla pravděpodobně přerušena v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="244b8-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="244b8-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="244b8-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="244b8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="244b8-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
