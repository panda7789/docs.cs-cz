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
ms.workload: dotnet
ms.openlocfilehash: 0d55500efbe808b2fce16e869422e727b8ed0b93
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="ca613-102">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca613-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="ca613-103">Poskytuje implementaci hostitele reprezentace Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="ca613-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ca613-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ca613-104">Methods</span></span>  
  
|<span data-ttu-id="ca613-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ca613-105">Method</span></span>|<span data-ttu-id="ca613-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ca613-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ca613-107">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="ca613-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="ca613-108">Obnoví aktuální `IHostManualEvent` instance do stavu signál.</span><span class="sxs-lookup"><span data-stu-id="ca613-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="ca613-109">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="ca613-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="ca613-110">Nastaví aktuální `IHostManualEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="ca613-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="ca613-111">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="ca613-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="ca613-112">Způsobí, že aktuální `IHostManualEvent` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="ca613-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ca613-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ca613-113">Requirements</span></span>  
 <span data-ttu-id="ca613-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca613-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca613-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ca613-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ca613-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ca613-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ca613-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca613-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca613-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca613-118">See Also</span></span>  
 [<span data-ttu-id="ca613-119">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca613-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="ca613-120">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca613-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="ca613-121">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca613-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="ca613-122">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ca613-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="ca613-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ca613-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
