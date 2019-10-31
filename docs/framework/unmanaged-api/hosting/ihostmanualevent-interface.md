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
ms.openlocfilehash: 8eba189d6dfca3781c28631a72a9af3c037efeda
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136785"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="87dc8-102">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87dc8-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="87dc8-103">Poskytuje implementaci reprezentace události ručního resetování hostitele.</span><span class="sxs-lookup"><span data-stu-id="87dc8-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87dc8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="87dc8-104">Methods</span></span>  
  
|<span data-ttu-id="87dc8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="87dc8-105">Method</span></span>|<span data-ttu-id="87dc8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="87dc8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87dc8-107">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="87dc8-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="87dc8-108">Obnoví aktuální instanci `IHostManualEvent` na stav bez signalizace.</span><span class="sxs-lookup"><span data-stu-id="87dc8-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="87dc8-109">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="87dc8-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="87dc8-110">Nastaví aktuální instanci `IHostManualEvent` na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="87dc8-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="87dc8-111">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="87dc8-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="87dc8-112">Způsobí, že aktuální instance `IHostManualEvent` počká, dokud není vlastněná, nebo dokud neuplyne zadaný čas.</span><span class="sxs-lookup"><span data-stu-id="87dc8-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87dc8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87dc8-113">Requirements</span></span>  
 <span data-ttu-id="87dc8-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87dc8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87dc8-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="87dc8-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87dc8-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="87dc8-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87dc8-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87dc8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87dc8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87dc8-118">See also</span></span>

- [<span data-ttu-id="87dc8-119">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87dc8-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="87dc8-120">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87dc8-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="87dc8-121">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87dc8-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="87dc8-122">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87dc8-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="87dc8-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="87dc8-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
