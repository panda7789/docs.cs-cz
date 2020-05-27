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
ms.openlocfilehash: db089a55128fa675ceedf157b046fe205d8c6b51
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804328"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="c54a4-102">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c54a4-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="c54a4-103">Poskytuje metody, které upozorňují na hostitele akcí, které modul CLR (Common Language Runtime) provede v případě přerušení, vypršení časového limitu nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="c54a4-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c54a4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c54a4-104">Methods</span></span>  
  
|<span data-ttu-id="c54a4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c54a4-105">Method</span></span>|<span data-ttu-id="c54a4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c54a4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c54a4-107">OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="c54a4-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="c54a4-108">Upozorní hostitele, že modul CLR má převzít výchozí akci určenou voláním metody [ICLRPolicyManager:: setdefaultaction –](iclrpolicymanager-setdefaultaction-method.md) v reakci na přerušení nebo <xref:System.AppDomain> uvolnění vlákna.</span><span class="sxs-lookup"><span data-stu-id="c54a4-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="c54a4-109">OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="c54a4-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="c54a4-110">Upozorní hostitele, že se chystá modul CLR, aby provedl akci určenou voláním [ICLRPolicyManager:: SetActionOnFailure –](iclrpolicymanager-setactiononfailure-method.md) v reakci na přidělení prostředků nebo selhání opětovného získávání.</span><span class="sxs-lookup"><span data-stu-id="c54a4-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="c54a4-111">OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="c54a4-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="c54a4-112">Upozorní hostitele, že se chystá modul CLR provést akci určenou voláním metody [ICLRPolicyManager:: SetActionOnTimeout –](iclrpolicymanager-setactionontimeout-method.md) v reakci na časový limit.</span><span class="sxs-lookup"><span data-stu-id="c54a4-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c54a4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c54a4-113">Requirements</span></span>  
 <span data-ttu-id="c54a4-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c54a4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c54a4-115">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c54a4-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c54a4-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c54a4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c54a4-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c54a4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54a4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c54a4-118">See also</span></span>

- [<span data-ttu-id="c54a4-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="c54a4-119">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="c54a4-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="c54a4-120">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="c54a4-121">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="c54a4-121">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="c54a4-122">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c54a4-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="c54a4-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="c54a4-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
