---
title: Počet nezdařených relací spolehlivého zasílání zpráv za sekundu
ms.date: 03/30/2017
ms.assetid: 8f8ca2eb-1be4-4b6a-aa78-fcd3ee145fe8
ms.openlocfilehash: 4dd247131182aca65a837095144673690cb134c8
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163940"
---
# <a name="reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="5ed5f-102">Počet nezdařených relací spolehlivého zasílání zpráv za sekundu</span><span class="sxs-lookup"><span data-stu-id="5ed5f-102">Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="5ed5f-103">Název čítače: v relacích spolehlivého zasílání zpráv došlo k chybě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="5ed5f-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="5ed5f-104">Popis</span><span class="sxs-lookup"><span data-stu-id="5ed5f-104">Description</span></span>  
 <span data-ttu-id="5ed5f-105">Počet relací spolehlivého zasílání zpráv, u kterých došlo k chybě v této službě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="5ed5f-105">Number of reliable messaging sessions that are faulted in this service in a second.</span></span>  
  
 <span data-ttu-id="5ed5f-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="5ed5f-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="5ed5f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="5ed5f-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
