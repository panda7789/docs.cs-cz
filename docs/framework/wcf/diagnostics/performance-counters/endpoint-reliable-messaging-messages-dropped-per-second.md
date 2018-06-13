---
title: 'Koncový bod: Vynechané zpráv spolehlivého zasílání zpráv za sekundu'
ms.date: 03/30/2017
ms.assetid: ea3c4fc0-1e0f-4863-8879-57bc6c113018
ms.openlocfilehash: a87e5fef0c13e239959a386f108af3c4cebae7f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33472281"
---
# <a name="endpoint-reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="c9588-102">Koncový bod: Vynechané zpráv spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="c9588-102">Endpoint: Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="c9588-103">Název čítače: Vyřadit relací spolehlivého zasílání zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="c9588-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="c9588-104">Popis</span><span class="sxs-lookup"><span data-stu-id="c9588-104">Description</span></span>  
 <span data-ttu-id="c9588-105">Celkový počet zpráv spolehlivého zasílání zpráv, které byly vynechány na tento koncový bod za sekundu.</span><span class="sxs-lookup"><span data-stu-id="c9588-105">Total number of reliable messaging messages that have been dropped at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="c9588-106">Tento čítač je typu čítače výkonu [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="c9588-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="c9588-107">(NE 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="c9588-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
