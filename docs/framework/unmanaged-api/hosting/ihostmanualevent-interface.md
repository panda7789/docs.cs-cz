---
title: IHostManualEvent – rozhraní
ms.date: 03/30/2017
api_name:
- IHostManualEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent
helpviewer_keywords:
- IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 300c2661-b7d1-4c39-b080-9ebdef0fd523
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53aaf4c23861666962e5567a6cf9eb9fffc6292f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438753"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="8b17f-102">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b17f-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="8b17f-103">Poskytuje implementaci hostitele reprezentace Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="8b17f-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8b17f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8b17f-104">Methods</span></span>  
  
|<span data-ttu-id="8b17f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8b17f-105">Method</span></span>|<span data-ttu-id="8b17f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8b17f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8b17f-107">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="8b17f-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="8b17f-108">Obnoví aktuální `IHostManualEvent` instance do stavu signál.</span><span class="sxs-lookup"><span data-stu-id="8b17f-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="8b17f-109">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="8b17f-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="8b17f-110">Nastaví aktuální `IHostManualEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="8b17f-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="8b17f-111">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="8b17f-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="8b17f-112">Způsobí, že aktuální `IHostManualEvent` instance počkat, dokud je vlastněná nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="8b17f-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b17f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8b17f-113">Requirements</span></span>  
 <span data-ttu-id="8b17f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b17f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b17f-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8b17f-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8b17f-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="8b17f-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8b17f-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b17f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b17f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b17f-118">See Also</span></span>  
 [<span data-ttu-id="8b17f-119">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b17f-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="8b17f-120">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b17f-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="8b17f-121">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b17f-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="8b17f-122">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8b17f-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="8b17f-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="8b17f-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
