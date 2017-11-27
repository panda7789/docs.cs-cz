---
title: "IHostManualEvent – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent
helpviewer_keywords: IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5c19125d96d5f4a9e91fc083d53f36ebebd2c569
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="b83d9-102">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b83d9-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="b83d9-103">Poskytuje implementaci hostitele reprezentace Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="b83d9-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b83d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b83d9-104">Methods</span></span>  
  
|<span data-ttu-id="b83d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b83d9-105">Method</span></span>|<span data-ttu-id="b83d9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b83d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b83d9-107">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="b83d9-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="b83d9-108">Obnoví aktuální `IHostManualEvent` instance do stavu signál.</span><span class="sxs-lookup"><span data-stu-id="b83d9-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="b83d9-109">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="b83d9-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="b83d9-110">Nastaví aktuální `IHostManualEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="b83d9-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="b83d9-111">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="b83d9-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="b83d9-112">Způsobí, že aktuální `IHostManualEvent` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="b83d9-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b83d9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b83d9-113">Requirements</span></span>  
 <span data-ttu-id="b83d9-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b83d9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b83d9-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b83d9-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b83d9-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b83d9-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b83d9-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b83d9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b83d9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b83d9-118">See Also</span></span>  
 [<span data-ttu-id="b83d9-119">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b83d9-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="b83d9-120">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b83d9-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="b83d9-121">Ihostsemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b83d9-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="b83d9-122">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b83d9-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="b83d9-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="b83d9-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
