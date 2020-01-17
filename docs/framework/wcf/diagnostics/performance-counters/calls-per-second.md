---
title: Počet volání za sekundu
ms.date: 03/30/2017
ms.assetid: 0efb5a94-d83b-4793-b529-6fcbedb65c43
ms.openlocfilehash: 94d499d70445bc9c162d9f6ee9aadb3a025c744f
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163576"
---
# <a name="calls-per-second"></a><span data-ttu-id="0abf0-102">Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="0abf0-102">Calls Per Second</span></span>
<span data-ttu-id="0abf0-103">Název čítače: počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="0abf0-103">Counter Name: Calls Per Second</span></span>  
  
## <a name="description"></a><span data-ttu-id="0abf0-104">Popis</span><span class="sxs-lookup"><span data-stu-id="0abf0-104">Description</span></span>  
 <span data-ttu-id="0abf0-105">Počet volání této operace za sekundu.</span><span class="sxs-lookup"><span data-stu-id="0abf0-105">Number of calls to this operation in a second.</span></span>  
  
 <span data-ttu-id="0abf0-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="0abf0-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="0abf0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="0abf0-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
