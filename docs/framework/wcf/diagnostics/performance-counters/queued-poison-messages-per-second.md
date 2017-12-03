---
title: "Počet poškozených zpráv za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2811cbcca7d4e11465191e5d25b820b4a7b15e4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="2d855-102">Počet poškozených zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="2d855-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="2d855-103">Název čítače: Počet poškozených zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="2d855-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2d855-104">Popis</span><span class="sxs-lookup"><span data-stu-id="2d855-104">Description</span></span>  
 <span data-ttu-id="2d855-105">Počet zpráv, které jsou označeny za sekundu s frontou zařazených do fronty přenosu v této služby.</span><span class="sxs-lookup"><span data-stu-id="2d855-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="2d855-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="2d855-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="2d855-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="2d855-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
