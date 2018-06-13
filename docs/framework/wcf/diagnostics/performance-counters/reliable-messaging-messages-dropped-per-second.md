---
title: Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 9a87ec509b19f0c566b50ae3672a6c3d2940ee12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33474191"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="8e011-102">Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="8e011-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="8e011-103">Název čítače: Vyřadit relací spolehlivého zasílání zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="8e011-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="8e011-104">Popis</span><span class="sxs-lookup"><span data-stu-id="8e011-104">Description</span></span>  
 <span data-ttu-id="8e011-105">Celkový počet zpráv spolehlivého zasílání zpráv, které byly vynechány v rámci této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="8e011-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="8e011-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="8e011-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="8e011-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="8e011-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
