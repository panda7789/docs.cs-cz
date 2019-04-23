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
ms.openlocfilehash: 864a8a4dd9f96da2fd0e0025848a910b4f8b0a70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180508"
---
# <a name="iactiononclrevent-interface"></a><span data-ttu-id="7142e-102">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7142e-102">IActionOnCLREvent Interface</span></span>
<span data-ttu-id="7142e-103">Poskytuje [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metodu, která provádí zpětná volání na události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7142e-103">Provides the [IActionOnCLREvent::OnEvent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) method, which performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7142e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7142e-104">Methods</span></span>  
  
|<span data-ttu-id="7142e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7142e-105">Method</span></span>|<span data-ttu-id="7142e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7142e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7142e-107">OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="7142e-107">OnEvent Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md)|<span data-ttu-id="7142e-108">Provede zpětné volání pro registrované události.</span><span class="sxs-lookup"><span data-stu-id="7142e-108">Performs a callback for a registered event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7142e-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7142e-109">Requirements</span></span>  
 <span data-ttu-id="7142e-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7142e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7142e-111">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7142e-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7142e-112">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7142e-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7142e-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7142e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7142e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7142e-114">See also</span></span>

- [<span data-ttu-id="7142e-115">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="7142e-115">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="7142e-116">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7142e-116">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="7142e-117">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7142e-117">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="7142e-118">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="7142e-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
