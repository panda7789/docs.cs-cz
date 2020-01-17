---
title: Počet zrušených zpracovaných operací za sekundu
ms.date: 03/30/2017
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
ms.openlocfilehash: d03f1faf7d2a00d02500fe9759ba940445d8eee3
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164018"
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="87287-102">Počet zrušených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="87287-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="87287-103">Název čítače: Počet zrušených zpracovaných operací za sekundu.</span><span class="sxs-lookup"><span data-stu-id="87287-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="87287-104">Popis</span><span class="sxs-lookup"><span data-stu-id="87287-104">Description</span></span>  
 <span data-ttu-id="87287-105">Počet transakčních operací, které byly v této službě přerušeny za sekundu.</span><span class="sxs-lookup"><span data-stu-id="87287-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="87287-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="87287-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="87287-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="87287-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
