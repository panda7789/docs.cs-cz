---
title: ICLRControl – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl
helpviewer_keywords:
- ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a06c1f4e1fcfe9c9c361a0e0bb2e8722577a13b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432892"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="6cd11-102">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-102">ICLRControl Interface</span></span>
<span data-ttu-id="6cd11-103">Poskytuje metody, které umožňují získat odkazy na hostitele a konfiguraci aspektů, modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="6cd11-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cd11-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6cd11-104">Methods</span></span>  
  
|<span data-ttu-id="6cd11-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-105">Method</span></span>|<span data-ttu-id="6cd11-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6cd11-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cd11-107">GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="6cd11-108">Získá ukazatele rozhraní k instanci jakýkoli z typů správce, které hostitele můžete použít ke konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6cd11-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="6cd11-109">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="6cd11-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="6cd11-110">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6cd11-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cd11-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cd11-111">Requirements</span></span>  
 <span data-ttu-id="6cd11-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd11-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd11-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6cd11-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cd11-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6cd11-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cd11-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd11-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd11-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cd11-116">See Also</span></span>  
 [<span data-ttu-id="6cd11-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="6cd11-118">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="6cd11-119">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="6cd11-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="6cd11-121">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="6cd11-122">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="6cd11-123">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="6cd11-124">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd11-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="6cd11-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6cd11-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
