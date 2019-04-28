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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf9d903b4e44ea7a185ad8b3b71b7a5da2f2bda3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760113"
---
# <a name="ihostpolicymanager-interface"></a><span data-ttu-id="9a048-102">IHostPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a048-102">IHostPolicyManager Interface</span></span>
<span data-ttu-id="9a048-103">Poskytuje metody, které upozornění na hostiteli akce, které provádí common language runtime (CLR) v případě klíčových přeruší, vypršení časového limitu nebo selhání.</span><span class="sxs-lookup"><span data-stu-id="9a048-103">Provides methods that notify the host of the actions the common language runtime (CLR) performs in case of aborts, timeouts, or failures.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9a048-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9a048-104">Methods</span></span>  
  
|<span data-ttu-id="9a048-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9a048-105">Method</span></span>|<span data-ttu-id="9a048-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9a048-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9a048-107">OnDefaultAction – metoda</span><span class="sxs-lookup"><span data-stu-id="9a048-107">OnDefaultAction Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ondefaultaction-method.md)|<span data-ttu-id="9a048-108">Upozorňuje hostitele, který modul CLR se chystá provést výchozí akci určené voláním [iclrpolicymanager::setdefaultaction –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) v reakci na vlákno přerušení nebo <xref:System.AppDomain> uvolnit.</span><span class="sxs-lookup"><span data-stu-id="9a048-108">Notifies the host that the CLR is about to take the default action specified by a call to [ICLRPolicyManager::SetDefaultAction](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setdefaultaction-method.md) in response to a thread abort or <xref:System.AppDomain> unload.</span></span>|  
|[<span data-ttu-id="9a048-109">OnFailure – metoda</span><span class="sxs-lookup"><span data-stu-id="9a048-109">OnFailure Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-onfailure-method.md)|<span data-ttu-id="9a048-110">Upozorňuje hostitele, který modul CLR se chystáte udělat akci určené voláním [iclrpolicymanager::setactiononfailure –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) v reakci na selhání přidělení nebo recyklaci prostředku.</span><span class="sxs-lookup"><span data-stu-id="9a048-110">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnFailure](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactiononfailure-method.md) in response to a resource allocation or reclamation failure.</span></span>|  
|[<span data-ttu-id="9a048-111">OnTimeout – metoda</span><span class="sxs-lookup"><span data-stu-id="9a048-111">OnTimeout Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-ontimeout-method.md)|<span data-ttu-id="9a048-112">Upozorňuje hostitele, který modul CLR se chystáte udělat akci určené voláním [iclrpolicymanager::setactionontimeout –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) v reakci na vypršení časového limitu.</span><span class="sxs-lookup"><span data-stu-id="9a048-112">Notifies the host that the CLR is about to take the action specified by a call to [ICLRPolicyManager::SetActionOnTimeout](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setactionontimeout-method.md) in response to a timeout.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a048-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a048-113">Requirements</span></span>  
 <span data-ttu-id="9a048-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a048-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a048-115">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a048-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a048-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a048-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a048-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a048-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a048-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a048-118">See also</span></span>

- [<span data-ttu-id="9a048-119">EClrFailure – výčet</span><span class="sxs-lookup"><span data-stu-id="9a048-119">EClrFailure Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [<span data-ttu-id="9a048-120">EClrOperation – výčet</span><span class="sxs-lookup"><span data-stu-id="9a048-120">EClrOperation Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [<span data-ttu-id="9a048-121">EPolicyAction – výčet</span><span class="sxs-lookup"><span data-stu-id="9a048-121">EPolicyAction Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [<span data-ttu-id="9a048-122">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a048-122">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="9a048-123">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="9a048-123">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
