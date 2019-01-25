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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f547d1bafa37c2cbb285a5d55cef8e1a6e29d0a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54688243"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="886a0-102">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="886a0-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="886a0-103">Poskytuje [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodu, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="886a0-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="886a0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="886a0-104">Methods</span></span>  
  
|<span data-ttu-id="886a0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="886a0-105">Method</span></span>|<span data-ttu-id="886a0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="886a0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="886a0-107">OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="886a0-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="886a0-108">Provede zpětné volání pro registrované události.</span><span class="sxs-lookup"><span data-stu-id="886a0-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="886a0-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="886a0-109">Requirements</span></span>  
 <span data-ttu-id="886a0-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="886a0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="886a0-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="886a0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="886a0-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="886a0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="886a0-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="886a0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="886a0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="886a0-114">See also</span></span>
- [<span data-ttu-id="886a0-115">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="886a0-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="886a0-116">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="886a0-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="886a0-117">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="886a0-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="886a0-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="886a0-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
