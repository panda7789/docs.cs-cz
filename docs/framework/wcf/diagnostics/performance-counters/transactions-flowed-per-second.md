---
title: Počet plynoucích transakcí za sekundu
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: e77aef4cfff1e64f112e720183675dfb7aa25d27
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392933"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="0f85c-102">Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="0f85c-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="0f85c-103">Název čítače: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="0f85c-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="0f85c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="0f85c-104">Description</span></span>  
 <span data-ttu-id="0f85c-105">Počet transakcí, které byly převedeny do této operace za sekundu.</span><span class="sxs-lookup"><span data-stu-id="0f85c-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="0f85c-106">Tento čítač se zvýší pokaždé, když je k dispozici v zpráva odeslaná do operace ID transakce.</span><span class="sxs-lookup"><span data-stu-id="0f85c-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="0f85c-107">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="0f85c-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0f85c-108">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="0f85c-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
