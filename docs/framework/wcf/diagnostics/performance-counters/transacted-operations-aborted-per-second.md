---
title: "Počet zrušených zpracovaných operací za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19fc993f-2b3d-4898-852e-3b98ec2153a5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d80d18ed1e3911b0603f930e45bda3dffaff1f75
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="7913d-102">Počet zrušených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="7913d-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="7913d-103">Název čítače: Transakční operace přerušených za sekundu.</span><span class="sxs-lookup"><span data-stu-id="7913d-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7913d-104">Popis</span><span class="sxs-lookup"><span data-stu-id="7913d-104">Description</span></span>  
 <span data-ttu-id="7913d-105">Počet transakcí operací, které bylo přerušeno v rámci této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="7913d-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="7913d-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="7913d-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="7913d-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="7913d-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
