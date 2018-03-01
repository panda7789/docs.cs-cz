---
title: "ICLROnEventManager – rozhraní"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 02a19a3daf72cdfa493b09fa984fe7b50865ed30
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="7d38a-102">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d38a-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="7d38a-103">Poskytuje metody, které umožňují hostitele registrace a zrušení registrace zpětných volání pro běžné události language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7d38a-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7d38a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7d38a-104">Methods</span></span>  
  
|<span data-ttu-id="7d38a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7d38a-105">Method</span></span>|<span data-ttu-id="7d38a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7d38a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d38a-107">RegisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="7d38a-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="7d38a-108">Zaregistruje zpětné volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="7d38a-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="7d38a-109">UnregisterActionOnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="7d38a-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="7d38a-110">Zruší registraci ukazatel dříve zaregistrovaný zpětného volání pro zadané události.</span><span class="sxs-lookup"><span data-stu-id="7d38a-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d38a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d38a-111">Remarks</span></span>  
 <span data-ttu-id="7d38a-112">Registrace a zrušení registrace zpětných volání událostí, hostitele získá odkaz na `ICLROnEventManager` voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="7d38a-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7d38a-113">Události popsané podle [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) může být aktivována více než jednou a z různých vláknech signál uvolnění nebo zakázání modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7d38a-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d38a-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d38a-114">Requirements</span></span>  
 <span data-ttu-id="7d38a-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d38a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d38a-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d38a-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d38a-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d38a-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d38a-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d38a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d38a-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d38a-119">See Also</span></span>  
 [<span data-ttu-id="7d38a-120">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="7d38a-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="7d38a-121">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d38a-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="7d38a-122">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d38a-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="7d38a-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7d38a-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
