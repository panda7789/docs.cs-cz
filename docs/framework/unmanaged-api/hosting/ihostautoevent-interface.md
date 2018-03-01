---
title: "IHostAutoEvent – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91e790cf7c97c0045535870c2d41d628f943a22d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="3a829-102">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a829-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="3a829-103">Poskytuje reprezentaci hostitele implementace události automatického vynulování.</span><span class="sxs-lookup"><span data-stu-id="3a829-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a829-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3a829-104">Methods</span></span>  
  
|<span data-ttu-id="3a829-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3a829-105">Method</span></span>|<span data-ttu-id="3a829-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3a829-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a829-107">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="3a829-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="3a829-108">Nastaví aktuální `IHostAutoEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="3a829-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="3a829-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="3a829-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="3a829-110">Způsobí, že aktuální `IHostAutoEvent` instance počkal vlastní události nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="3a829-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a829-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a829-111">Requirements</span></span>  
 <span data-ttu-id="3a829-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a829-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a829-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3a829-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3a829-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3a829-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3a829-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a829-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a829-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a829-116">See Also</span></span>  
 [<span data-ttu-id="3a829-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a829-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="3a829-118">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a829-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="3a829-119">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a829-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="3a829-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="3a829-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
