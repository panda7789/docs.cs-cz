---
title: 'Koncový bod: počet relací spolehlivého zasílání zpráv s chybou za sekundu'
ms.date: 03/30/2017
ms.assetid: e9ae808a-7e1f-46b0-9560-d5a866be6d6e
ms.openlocfilehash: 26fd8236af6516716f7cf9c7c06f669473bdfc3a
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76163186"
---
# <a name="endpoint-reliable-messaging-sessions-faulted-per-second"></a><span data-ttu-id="a2d5a-102">Koncový bod: počet relací spolehlivého zasílání zpráv s chybou za sekundu</span><span class="sxs-lookup"><span data-stu-id="a2d5a-102">Endpoint: Reliable Messaging Sessions Faulted Per Second</span></span>
<span data-ttu-id="a2d5a-103">Název čítače: v relacích spolehlivého zasílání zpráv došlo k chybě za sekundu.</span><span class="sxs-lookup"><span data-stu-id="a2d5a-103">Counter Name: Reliable Messaging Sessions Faulted Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="a2d5a-104">Popis</span><span class="sxs-lookup"><span data-stu-id="a2d5a-104">Description</span></span>  
 <span data-ttu-id="a2d5a-105">Počet relací spolehlivého zasílání zpráv, u kterých došlo k chybě v tomto koncovém bodu za sekundu.</span><span class="sxs-lookup"><span data-stu-id="a2d5a-105">Number of reliable messaging sessions that are faulted at this endpoint in a second.</span></span>  
  
 <span data-ttu-id="a2d5a-106">Tento čítač má typ čítače výkonu [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), jehož hodnota se počítá pomocí následujícího vzorce.</span><span class="sxs-lookup"><span data-stu-id="a2d5a-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="a2d5a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="a2d5a-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
