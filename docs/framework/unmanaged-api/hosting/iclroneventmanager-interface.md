---
title: "ICLROnEventManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLROnEventManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLROnEventManager
helpviewer_keywords: ICLROnEventManager interface [.NET Framework hosting]
ms.assetid: 9e15a0c1-8ab6-43d0-ae28-6ec7a4edd913
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d3f792af3e01d476768961928272cb6166a144f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclroneventmanager-interface"></a><span data-ttu-id="1765c-102">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1765c-102">ICLROnEventManager Interface</span></span>
<span data-ttu-id="1765c-103">Poskytuje metody, které umožňují hostitele registrace a zrušení registrace zpětných volání pro běžné události language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="1765c-103">Provides methods that allow the host to register and unregister callbacks for common language runtime (CLR) events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1765c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1765c-104">Methods</span></span>  
  
|<span data-ttu-id="1765c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1765c-105">Method</span></span>|<span data-ttu-id="1765c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1765c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1765c-107">Registeractiononevent – metoda</span><span class="sxs-lookup"><span data-stu-id="1765c-107">RegisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md)|<span data-ttu-id="1765c-108">Zaregistruje zpětné volání ukazatel zadané události.</span><span class="sxs-lookup"><span data-stu-id="1765c-108">Registers a callback pointer for the specified event.</span></span>|  
|[<span data-ttu-id="1765c-109">Unregisteractiononevent – metoda</span><span class="sxs-lookup"><span data-stu-id="1765c-109">UnregisterActionOnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-unregisteractiononevent-method.md)|<span data-ttu-id="1765c-110">Zruší registraci ukazatel dříve zaregistrovaný zpětného volání pro zadané události.</span><span class="sxs-lookup"><span data-stu-id="1765c-110">Unregisters a previously registered callback pointer for the specified event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1765c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1765c-111">Remarks</span></span>  
 <span data-ttu-id="1765c-112">Registrace a zrušení registrace zpětných volání událostí, hostitele získá odkaz na `ICLROnEventManager` voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="1765c-112">To register and unregister event callbacks, the host gets a reference to `ICLROnEventManager` by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1765c-113">Události popsané podle [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) může být aktivována více než jednou a z různých vláknech signál uvolnění nebo zakázání modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="1765c-113">The events described by [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1765c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1765c-114">Requirements</span></span>  
 <span data-ttu-id="1765c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1765c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1765c-116">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1765c-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1765c-117">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1765c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1765c-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1765c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1765c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1765c-119">See Also</span></span>  
 [<span data-ttu-id="1765c-120">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="1765c-120">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="1765c-121">Iactiononclrevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1765c-121">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="1765c-122">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1765c-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="1765c-123">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="1765c-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
