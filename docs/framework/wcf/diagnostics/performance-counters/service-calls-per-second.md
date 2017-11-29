---
title: "Služba: Počet volání za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 940249c4ec0317013efcb03aafc11d384ec0363f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-calls-per-second"></a><span data-ttu-id="354de-102">Služba: Počet volání za sekundu</span><span class="sxs-lookup"><span data-stu-id="354de-102">Service: Calls Per Second</span></span>
<span data-ttu-id="354de-103">Název čítače: Počet volání za sekundu.</span><span class="sxs-lookup"><span data-stu-id="354de-103">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="354de-104">Popis</span><span class="sxs-lookup"><span data-stu-id="354de-104">Description</span></span>  
 <span data-ttu-id="354de-105">Počet volání k této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="354de-105">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="354de-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="354de-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="354de-107">(Ne 1 - N 0) / ((D 1 -D 0) / F) kde čítači (ne) představuje počet operací prováděné během posledního ukázkového intervalu, představuje jmenovatel (D) během posledního ukázkového intervalu, uplynulý čas počet rysky a F je četnost o rysky.</span><span class="sxs-lookup"><span data-stu-id="354de-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
