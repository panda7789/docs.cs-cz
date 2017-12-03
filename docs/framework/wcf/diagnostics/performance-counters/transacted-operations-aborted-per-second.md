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
ms.openlocfilehash: a54b84f2fa0ab9c7531a17e69b10f78c725255ef
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="transacted-operations-aborted-per-second"></a><span data-ttu-id="fdef2-102">Počet zrušených zpracovaných operací za sekundu</span><span class="sxs-lookup"><span data-stu-id="fdef2-102">Transacted Operations Aborted Per Second</span></span>
<span data-ttu-id="fdef2-103">Název čítače: Transakční operace přerušených za sekundu.</span><span class="sxs-lookup"><span data-stu-id="fdef2-103">Counter Name: Transacted Operations Aborted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="fdef2-104">Popis</span><span class="sxs-lookup"><span data-stu-id="fdef2-104">Description</span></span>  
 <span data-ttu-id="fdef2-105">Počet transakcí operací, které bylo přerušeno v rámci této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="fdef2-105">Number of transactional operations that have been aborted in this service in a second.</span></span>  
  
 <span data-ttu-id="fdef2-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="fdef2-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="fdef2-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="fdef2-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
