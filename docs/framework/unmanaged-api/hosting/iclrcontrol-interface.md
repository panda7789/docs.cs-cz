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
ms.openlocfilehash: f70e7958cc9ac198738ed72732fe7b6563c89067
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59175419"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="66c9e-102">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-102">ICLRControl Interface</span></span>
<span data-ttu-id="66c9e-103">Poskytuje metody, které umožňují získat odkazy na hostitele a konfigurovat aspekty modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="66c9e-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="66c9e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="66c9e-104">Methods</span></span>  
  
|<span data-ttu-id="66c9e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="66c9e-105">Method</span></span>|<span data-ttu-id="66c9e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="66c9e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="66c9e-107">GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="66c9e-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="66c9e-108">Získá ukazatel rozhraní k instanci správce typů, které hostitele můžete použít ke konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="66c9e-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="66c9e-109">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="66c9e-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="66c9e-110">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="66c9e-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="66c9e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66c9e-111">Requirements</span></span>  
 <span data-ttu-id="66c9e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c9e-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="66c9e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="66c9e-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="66c9e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="66c9e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c9e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c9e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66c9e-116">See also</span></span>

- [<span data-ttu-id="66c9e-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="66c9e-118">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="66c9e-119">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="66c9e-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="66c9e-121">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="66c9e-122">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="66c9e-123">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="66c9e-124">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66c9e-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="66c9e-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="66c9e-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
