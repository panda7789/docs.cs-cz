---
title: Počet poškozených zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: d193fdd1-02f1-44a0-906e-f632a8f574c3
ms.openlocfilehash: 6407cce120f5d534f88a12591ea2ad09bb5130d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33473256"
---
# <a name="queued-poison-messages-per-second"></a><span data-ttu-id="da036-102">Počet poškozených zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="da036-102">Queued Poison Messages Per Second</span></span>
<span data-ttu-id="da036-103">Název čítače: Počet poškozených zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="da036-103">Counter Name: Queued Poison Messages Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="da036-104">Popis</span><span class="sxs-lookup"><span data-stu-id="da036-104">Description</span></span>  
 <span data-ttu-id="da036-105">Počet zpráv, které jsou označeny za sekundu s frontou zařazených do fronty přenosu v této služby.</span><span class="sxs-lookup"><span data-stu-id="da036-105">Number of messages that are marked poisoned by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="da036-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="da036-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="da036-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="da036-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
