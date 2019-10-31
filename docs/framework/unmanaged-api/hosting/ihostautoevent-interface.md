---
title: IHostAutoEvent – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 2b191243ea03adcfecaadbd3a5871e1773b28bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124455"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="d9d4f-102">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9d4f-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="d9d4f-103">Poskytuje reprezentaci implementace události automatického resetování hostitele.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9d4f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d9d4f-104">Methods</span></span>  
  
|<span data-ttu-id="d9d4f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d9d4f-105">Method</span></span>|<span data-ttu-id="d9d4f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d9d4f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9d4f-107">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="d9d4f-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="d9d4f-108">Nastaví aktuální instanci `IHostAutoEvent` na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="d9d4f-109">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="d9d4f-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="d9d4f-110">Způsobí, že aktuální instance `IHostAutoEvent` počká, dokud událost nevlastníte, nebo dokud neuplyne zadaný čas.</span><span class="sxs-lookup"><span data-stu-id="d9d4f-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d9d4f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9d4f-111">Requirements</span></span>  
 <span data-ttu-id="d9d4f-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9d4f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9d4f-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d9d4f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d9d4f-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d9d4f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d9d4f-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9d4f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d4f-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9d4f-116">See also</span></span>

- [<span data-ttu-id="d9d4f-117">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9d4f-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="d9d4f-118">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9d4f-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="d9d4f-119">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d9d4f-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="d9d4f-120">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="d9d4f-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
