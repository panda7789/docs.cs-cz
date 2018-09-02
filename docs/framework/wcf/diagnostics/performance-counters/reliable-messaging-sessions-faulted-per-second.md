---
title: Počet nezdařených relací spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: c77d6a5f12dcce15dba94e2f63025a219ebcc6fd
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420716"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="11aa5-102">Počet nezdařených relací spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="11aa5-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="11aa5-103">Název čítače: Relací spolehlivého zasílání zpráv s chybou za sekundu.</span><span class="sxs-lookup"><span data-stu-id="11aa5-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="11aa5-104">Popis</span><span class="sxs-lookup"><span data-stu-id="11aa5-104">Description</span></span>  
 <span data-ttu-id="11aa5-105">Počet relací spolehlivého zasílání zpráv, které jsou s chybou v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="11aa5-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="11aa5-106">Tento čítač je typ čítače výkonu [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), jehož hodnota je vypočítána pomocí tohoto vzorce.</span><span class="sxs-lookup"><span data-stu-id="11aa5-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="11aa5-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="11aa5-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
