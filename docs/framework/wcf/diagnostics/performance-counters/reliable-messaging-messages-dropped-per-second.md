---
title: Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: a11b0b80-b242-48e1-b0bb-7f756db5486b
ms.openlocfilehash: 7722b32f99b302c5c272e095033879c9e04c7ee1
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877791"
---
# <a name="reliable-messaging-messages-dropped-per-second"></a><span data-ttu-id="b75b3-102">Počet ztracených zpráv spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="b75b3-102">Reliable Messaging Messages Dropped Per Second</span></span>
<span data-ttu-id="b75b3-103">Název čítače: Relací spolehlivého zasílání zpráv za sekundu.</span><span class="sxs-lookup"><span data-stu-id="b75b3-103">Counter Name: Reliable Messaging Sessions Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b75b3-104">Popis</span><span class="sxs-lookup"><span data-stu-id="b75b3-104">Description</span></span>  
 <span data-ttu-id="b75b3-105">Celkový počet spolehlivého zasílání zpráv, které byly vynechány v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="b75b3-105">Total number of reliable messaging messages that have been dropped in this service in a second.</span></span>  
  
 <span data-ttu-id="b75b3-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="b75b3-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="b75b3-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="b75b3-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
