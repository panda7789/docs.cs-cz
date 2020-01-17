---
title: Počet instancí za sekundu
ms.date: 03/30/2017
ms.assetid: 74579397-1058-4278-80cf-2d00854a480f
ms.openlocfilehash: 3ae0b83066b22187ce062596a62e9d17aa2acd45
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163797"
---
# <a name="instances-per-second"></a><span data-ttu-id="10040-102">Počet instancí za sekundu</span><span class="sxs-lookup"><span data-stu-id="10040-102">Instances Per Second</span></span>
<span data-ttu-id="10040-103">Název čítače: počet instancí vytvořených za sekundu.</span><span class="sxs-lookup"><span data-stu-id="10040-103">Counter Name: Instances Created Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="10040-104">Popis</span><span class="sxs-lookup"><span data-stu-id="10040-104">Description</span></span>  
 <span data-ttu-id="10040-105">Celkový počet instancí služby vytvořených za sekundu</span><span class="sxs-lookup"><span data-stu-id="10040-105">Total number of service instances created in a second.</span></span>  
  
 <span data-ttu-id="10040-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="10040-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="10040-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="10040-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
