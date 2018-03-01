---
title: "IActionOnCLREvent – rozhraní"
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
- IActionOnCLREvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent
helpviewer_keywords:
- IActionOnCLREvent interface [.NET Framework hosting]
ms.assetid: b5f9b41e-7301-429c-911f-21d5422292b3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4b51784f07a90faa9eeb29c18a784d4fbc2c4654
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="89d58-102">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d58-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="89d58-103">Poskytuje [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodě, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="89d58-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89d58-104">Metody</span><span class="sxs-lookup"><span data-stu-id="89d58-104">Methods</span></span>  
  
|<span data-ttu-id="89d58-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="89d58-105">Method</span></span>|<span data-ttu-id="89d58-106">Popis</span><span class="sxs-lookup"><span data-stu-id="89d58-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89d58-107">OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="89d58-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="89d58-108">Provede zpětné volání pro registrované událost.</span><span class="sxs-lookup"><span data-stu-id="89d58-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89d58-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89d58-109">Requirements</span></span>  
 <span data-ttu-id="89d58-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89d58-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89d58-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89d58-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89d58-112">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89d58-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89d58-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89d58-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d58-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="89d58-114">See Also</span></span>  
 [<span data-ttu-id="89d58-115">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="89d58-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)  
 [<span data-ttu-id="89d58-116">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d58-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="89d58-117">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89d58-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="89d58-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="89d58-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
