---
title: "ICLRControl – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl
helpviewer_keywords: ICLRControl interface [.NET Framework hosting]
ms.assetid: a24fd905-1fa6-45a0-ad65-e9e2ee58861e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98b41ea0062534d9e990a7fe366e8f746ae87f38
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="bee2e-102">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-102">ICLRControl Interface</span></span>
<span data-ttu-id="bee2e-103">Poskytuje metody, které umožňují získat odkazy na hostitele a konfiguraci aspektů, modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="bee2e-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bee2e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bee2e-104">Methods</span></span>  
  
|<span data-ttu-id="bee2e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bee2e-105">Method</span></span>|<span data-ttu-id="bee2e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bee2e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bee2e-107">Getclrmanager – metoda</span><span class="sxs-lookup"><span data-stu-id="bee2e-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="bee2e-108">Získá ukazatele rozhraní k instanci jakýkoli z typů správce, které hostitele můžete použít ke konfiguraci modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="bee2e-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="bee2e-109">Setappdomainmanagertype – metoda</span><span class="sxs-lookup"><span data-stu-id="bee2e-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="bee2e-110">Nastaví typ odvozený z <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bee2e-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bee2e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bee2e-111">Requirements</span></span>  
 <span data-ttu-id="bee2e-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee2e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee2e-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bee2e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bee2e-114">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bee2e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bee2e-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee2e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee2e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="bee2e-116">See Also</span></span>  
 [<span data-ttu-id="bee2e-117">Iclrassemblyidentitymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 [<span data-ttu-id="bee2e-118">Iclrdebugmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="bee2e-119">Iclrgcmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="bee2e-120">Iclrhostbindingpolicymanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 [<span data-ttu-id="bee2e-121">Iclrhostprotectionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 [<span data-ttu-id="bee2e-122">Iclroneventmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 [<span data-ttu-id="bee2e-123">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [<span data-ttu-id="bee2e-124">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee2e-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 [<span data-ttu-id="bee2e-125">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="bee2e-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
