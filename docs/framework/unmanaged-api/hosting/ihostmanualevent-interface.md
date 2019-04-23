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
ms.openlocfilehash: ad580f7cab81323e09a24dc12db39f223be3aeb4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59208628"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="5979c-102">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5979c-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="5979c-103">Poskytuje implementaci hostitele reprezentace Ruční vynulování události.</span><span class="sxs-lookup"><span data-stu-id="5979c-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5979c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5979c-104">Methods</span></span>  
  
|<span data-ttu-id="5979c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5979c-105">Method</span></span>|<span data-ttu-id="5979c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5979c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5979c-107">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="5979c-107">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-reset-method.md)|<span data-ttu-id="5979c-108">Obnoví aktuální `IHostManualEvent` instance do nesignálového stavu.</span><span class="sxs-lookup"><span data-stu-id="5979c-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="5979c-109">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="5979c-109">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-set-method.md)|<span data-ttu-id="5979c-110">Nastaví aktuální `IHostManualEvent` instance do signalizovaného stavu.</span><span class="sxs-lookup"><span data-stu-id="5979c-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="5979c-111">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="5979c-111">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-wait-method.md)|<span data-ttu-id="5979c-112">Způsobí, že aktuální `IHostManualEvent` instance počkat, dokud je ve vlastnictví nebo zadaného množství času po uplynutí předem.</span><span class="sxs-lookup"><span data-stu-id="5979c-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5979c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5979c-113">Requirements</span></span>  
 <span data-ttu-id="5979c-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5979c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5979c-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5979c-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5979c-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5979c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5979c-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5979c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5979c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5979c-118">See also</span></span>

- [<span data-ttu-id="5979c-119">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5979c-119">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="5979c-120">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5979c-120">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="5979c-121">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5979c-121">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)
- [<span data-ttu-id="5979c-122">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5979c-122">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="5979c-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="5979c-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
