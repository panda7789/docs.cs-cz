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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce34295e5ec318bcff9887765c46bde59066ab4e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="4b18c-102">Počet poškozených zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="4b18c-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="4b18c-103">Název čítače: Počet poškozených zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="4b18c-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4b18c-104">Popis</span><span class="sxs-lookup"><span data-stu-id="4b18c-104">Description</span></span>  
 <span data-ttu-id="4b18c-105">Počet zpráv, které jsou označeny za sekundu s frontou zařazených do fronty přenosu v této služby.</span><span class="sxs-lookup"><span data-stu-id="4b18c-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="4b18c-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="4b18c-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="4b18c-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="4b18c-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
