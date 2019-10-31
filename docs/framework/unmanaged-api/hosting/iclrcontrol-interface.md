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
ms.openlocfilehash: 914a2f6103fb0ffb9a7b9fcb895ecf0cd62f3c43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126598"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="2487a-102">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-102">ICLRControl Interface</span></span>
<span data-ttu-id="2487a-103">Poskytuje metody, které umožňují hostiteli získat odkazy na a konfigurovat aspekty modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="2487a-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2487a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2487a-104">Methods</span></span>  
  
|<span data-ttu-id="2487a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2487a-105">Method</span></span>|<span data-ttu-id="2487a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2487a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2487a-107">GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="2487a-107">GetCLRManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="2487a-108">Získá ukazatel rozhraní na instanci kteréhokoli typu správce, který může hostitel použít ke konfiguraci CLR.</span><span class="sxs-lookup"><span data-stu-id="2487a-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="2487a-109">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="2487a-109">SetAppDomainManagerType Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="2487a-110">Nastaví typ odvozený od <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2487a-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2487a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2487a-111">Requirements</span></span>  
 <span data-ttu-id="2487a-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2487a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2487a-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2487a-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2487a-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2487a-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2487a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2487a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2487a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2487a-116">See also</span></span>

- [<span data-ttu-id="2487a-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-117">ICLRAssemblyIdentityManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="2487a-118">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-118">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="2487a-119">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-119">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="2487a-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-120">ICLRHostBindingPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="2487a-121">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-121">ICLRHostProtectionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="2487a-122">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-122">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="2487a-123">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-123">ICLRPolicyManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [<span data-ttu-id="2487a-124">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2487a-124">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [<span data-ttu-id="2487a-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="2487a-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
