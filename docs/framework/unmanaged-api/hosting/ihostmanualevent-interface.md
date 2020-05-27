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
ms.openlocfilehash: 7c46f00063cdf9281a5f1080594e8d6dbc6c101e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804598"
---
# <a name="ihostmanualevent-interface"></a><span data-ttu-id="6ebd8-102">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebd8-102">IHostManualEvent Interface</span></span>
<span data-ttu-id="6ebd8-103">Poskytuje implementaci reprezentace události ručního resetování hostitele.</span><span class="sxs-lookup"><span data-stu-id="6ebd8-103">Provides the host's implementation of a representation of a manual reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6ebd8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6ebd8-104">Methods</span></span>  
  
|<span data-ttu-id="6ebd8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6ebd8-105">Method</span></span>|<span data-ttu-id="6ebd8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6ebd8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6ebd8-107">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="6ebd8-107">Reset Method</span></span>](ihostmanualevent-reset-method.md)|<span data-ttu-id="6ebd8-108">Obnoví aktuální `IHostManualEvent` instanci na stav bez signalizace.</span><span class="sxs-lookup"><span data-stu-id="6ebd8-108">Resets the current `IHostManualEvent` instance to a non-signaled state.</span></span>|  
|[<span data-ttu-id="6ebd8-109">Set – metoda</span><span class="sxs-lookup"><span data-stu-id="6ebd8-109">Set Method</span></span>](ihostmanualevent-set-method.md)|<span data-ttu-id="6ebd8-110">Nastaví aktuální `IHostManualEvent` instanci na signálový stav.</span><span class="sxs-lookup"><span data-stu-id="6ebd8-110">Sets the current `IHostManualEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="6ebd8-111">Wait – metoda</span><span class="sxs-lookup"><span data-stu-id="6ebd8-111">Wait Method</span></span>](ihostmanualevent-wait-method.md)|<span data-ttu-id="6ebd8-112">Způsobí, že aktuální `IHostManualEvent` instance počká, až bude ve vlastnictví, nebo zadanou dobu uplyne.</span><span class="sxs-lookup"><span data-stu-id="6ebd8-112">Causes the current `IHostManualEvent` instance to wait until it is owned, or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ebd8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6ebd8-113">Requirements</span></span>  
 <span data-ttu-id="6ebd8-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ebd8-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ebd8-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6ebd8-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6ebd8-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6ebd8-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6ebd8-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ebd8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebd8-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ebd8-118">See also</span></span>

- [<span data-ttu-id="6ebd8-119">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebd8-119">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="6ebd8-120">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebd8-120">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="6ebd8-121">IHostSemaphore – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebd8-121">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="6ebd8-122">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6ebd8-122">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
- [<span data-ttu-id="6ebd8-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6ebd8-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
