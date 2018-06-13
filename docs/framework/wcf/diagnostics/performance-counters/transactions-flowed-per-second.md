---
title: Počet plynoucích transakcí za sekundu
ms.date: 03/30/2017
ms.assetid: b9f661e1-576c-48fc-9fdf-91853e0749e8
ms.openlocfilehash: a71095b9fdd16d7e220be8a0aeb0a746bb50527e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472915"
---
# <a name="transactions-flowed-per-second"></a><span data-ttu-id="37b1f-102">Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="37b1f-102">Transactions Flowed Per Second</span></span>
<span data-ttu-id="37b1f-103">Název čítače: Počet plynoucích transakcí za sekundu</span><span class="sxs-lookup"><span data-stu-id="37b1f-103">Counter Name:  Transactions Flowed Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="37b1f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="37b1f-104">Description</span></span>  
 <span data-ttu-id="37b1f-105">Počet transakcí plynoucích s touto operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="37b1f-105">Number of transactions flowed to this operation in a second.</span></span> <span data-ttu-id="37b1f-106">Tento čítač se zvýší, když je součástí zprávy, která je odeslána operaci ID transakce.</span><span class="sxs-lookup"><span data-stu-id="37b1f-106">This counter is incremented any time a transaction ID is present in a message that is sent to the operation.</span></span>  
  
 <span data-ttu-id="37b1f-107">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="37b1f-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="37b1f-108">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="37b1f-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
