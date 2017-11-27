---
title: "Počet zpráv vyřazených z fronty za sekundu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d7386b2f7c6d78dde41c88c66d216b99cc21050
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="da60a-102">Počet zpráv vyřazených z fronty za sekundu</span><span class="sxs-lookup"><span data-stu-id="da60a-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="da60a-103">Název čítače: Zařadit do fronty ztracených zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="da60a-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="da60a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="da60a-104">Description</span></span>  
 <span data-ttu-id="da60a-105">Počet zpráv, které jsou vynechány podle zařazených do fronty přenosu v této služby za sekundu.</span><span class="sxs-lookup"><span data-stu-id="da60a-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="da60a-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="da60a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="da60a-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="da60a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
