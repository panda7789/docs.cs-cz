---
title: IHostPolicyManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostPolicyManager
helpviewer_keywords:
- IHostPolicyManager interface [.NET Framework hosting]
ms.assetid: 8c4aa124-5e00-46d9-b1e8-57ba6574bb0d
topic_type:
- apiref
ms.openlocfilehash: 6ba7b7adc104db528293d77c3591370c6ce02c25
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128601"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="def28-102">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="def28-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="def28-103">Poskytuje metody, které upozorňují na hostitele akcí, které modul CLR (Common Language Runtime) provede v případě přerušení, vypršení časového limitu nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="def28-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="def28-104">Metody</span><span class="sxs-lookup"><span data-stu-id="def28-104">Methods</span></span>  
  
|<span data-ttu-id="def28-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="def28-105">Method</span></span>|<span data-ttu-id="def28-106">Popis</span><span class="sxs-lookup"><span data-stu-id="def28-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="def28-107">OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="def28-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="def28-108">Upozorní hostitele, že modul CLR má převzít výchozí akci určenou voláním metody [ICLRPolicyManager:: setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení vlákna nebo <xref:System.AppDomain> uvolnění.</span><span class="sxs-lookup"><span data-stu-id="def28-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="def28-109">OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="def28-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="def28-110">Upozorní hostitele, že se chystá modul CLR, aby provedl akci určenou voláním [ICLRPolicyManager:: SetActionOnFailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) v reakci na přidělení prostředků nebo selhání opětovného získávání.</span><span class="sxs-lookup"><span data-stu-id="def28-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="def28-111">OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="def28-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="def28-112">Upozorní hostitele, že se chystá modul CLR provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="def28-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="def28-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="def28-113">Requirements</span></span>  
 <span data-ttu-id="def28-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="def28-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="def28-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="def28-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="def28-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="def28-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="def28-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="def28-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="def28-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="def28-118">See also</span></span>

- [<span data-ttu-id="def28-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="def28-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="def28-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="def28-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="def28-121">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="def28-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="def28-122">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="def28-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="def28-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="def28-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
