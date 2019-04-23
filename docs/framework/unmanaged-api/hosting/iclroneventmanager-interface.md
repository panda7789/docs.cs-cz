---
title: ICLROnEventManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLROnEventManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager
helpviewer_keywords:
- ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7486a094deab16ebbc05f19f1b652126479ce11c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182998"
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="eb8f3-102">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb8f3-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="eb8f3-103">Poskytuje metody, které umožňují hostitele tak, aby vytvářet a rušit registraci zpětná volání pro common language runtime (CLR) události.</span><span class="sxs-lookup"><span data-stu-id="eb8f3-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eb8f3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="eb8f3-104">Methods</span></span>  
  
|<span data-ttu-id="eb8f3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="eb8f3-105">Method</span></span>|<span data-ttu-id="eb8f3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="eb8f3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eb8f3-107">RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="eb8f3-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="eb8f3-108">Zaregistruje zpětné volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="eb8f3-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="eb8f3-109">UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="eb8f3-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="eb8f3-110">Zrušení registrace již registrovaného zpětného volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="eb8f3-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb8f3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb8f3-111">Remarks</span></span>  
 <span data-ttu-id="eb8f3-112">Chcete-li vytvářet a rušit registraci zpětná volání události, hostitel získá odkaz na `ICLROnEventManager` voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="eb8f3-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb8f3-113">Události popisované v [eclrevent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) může být aktivována více než jednou a z různých vláken, který signalizuje, že uvolnění z paměti nebo vypnutí CLR.</span><span class="sxs-lookup"><span data-stu-id="eb8f3-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb8f3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb8f3-114">Requirements</span></span>  
 <span data-ttu-id="eb8f3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb8f3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb8f3-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="eb8f3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="eb8f3-117">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb8f3-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="eb8f3-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb8f3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb8f3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb8f3-119">See also</span></span>

- [<span data-ttu-id="eb8f3-120">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="eb8f3-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="eb8f3-121">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb8f3-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="eb8f3-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb8f3-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="eb8f3-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="eb8f3-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
