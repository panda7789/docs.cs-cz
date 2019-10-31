---
title: IActionOnCLREvent – rozhraní
ms.date: 03/30/2017
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
ms.openlocfilehash: 9277fe2c241ce4f502339de826dccd08a2ce8055
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126962"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="0873d-102">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0873d-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="0873d-103">Poskytuje metodu [IActionOnCLREvent –::](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) ICLROnEventManager, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání metody [:: RegisterActionOnEvent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0873d-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0873d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0873d-104">Methods</span></span>  
  
|<span data-ttu-id="0873d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0873d-105">Method</span></span>|<span data-ttu-id="0873d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0873d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0873d-107">OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="0873d-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="0873d-108">Provede zpětné volání pro registrovanou událost.</span><span class="sxs-lookup"><span data-stu-id="0873d-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0873d-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0873d-109">Requirements</span></span>  
 <span data-ttu-id="0873d-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0873d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0873d-111">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0873d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0873d-112">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0873d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0873d-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0873d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0873d-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0873d-114">See also</span></span>

- [<span data-ttu-id="0873d-115">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="0873d-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="0873d-116">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0873d-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="0873d-117">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0873d-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="0873d-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="0873d-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
