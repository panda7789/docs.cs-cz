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
ms.openlocfilehash: 54748fdeaf911591c21f4495335e54c777878f04
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615833"
---
# <a name="iclrcontrol-interface"></a><span data-ttu-id="18fcd-102">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-102">ICLRControl Interface</span></span>
<span data-ttu-id="18fcd-103">Poskytuje metody, které umožňují hostiteli získat odkazy na a konfigurovat aspekty modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="18fcd-103">Provides methods that allow a host to get references to, and configure aspects of, the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18fcd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="18fcd-104">Methods</span></span>  
  
|<span data-ttu-id="18fcd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="18fcd-105">Method</span></span>|<span data-ttu-id="18fcd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="18fcd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18fcd-107">GetCLRManager – metoda</span><span class="sxs-lookup"><span data-stu-id="18fcd-107">GetCLRManager Method</span></span>](iclrcontrol-getclrmanager-method.md)|<span data-ttu-id="18fcd-108">Získá ukazatel rozhraní na instanci kteréhokoli typu správce, který může hostitel použít ke konfiguraci CLR.</span><span class="sxs-lookup"><span data-stu-id="18fcd-108">Gets an interface pointer to an instance of any of the manager types the host can use to configure the CLR.</span></span>|  
|[<span data-ttu-id="18fcd-109">SetAppDomainManagerType – metoda</span><span class="sxs-lookup"><span data-stu-id="18fcd-109">SetAppDomainManagerType Method</span></span>](iclrcontrol-setappdomainmanagertype-method.md)|<span data-ttu-id="18fcd-110">Nastaví typ odvozený od <xref:System.AppDomainManager> jako typ pro správce domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="18fcd-110">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18fcd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18fcd-111">Requirements</span></span>  
 <span data-ttu-id="18fcd-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18fcd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18fcd-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18fcd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18fcd-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="18fcd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18fcd-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18fcd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18fcd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="18fcd-116">See also</span></span>

- [<span data-ttu-id="18fcd-117">ICLRAssemblyIdentityManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="18fcd-118">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-118">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="18fcd-119">ICLRGCManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-119">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="18fcd-120">ICLRHostBindingPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-120">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
- [<span data-ttu-id="18fcd-121">ICLRHostProtectionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-121">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="18fcd-122">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-122">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="18fcd-123">ICLRPolicyManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-123">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="18fcd-124">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18fcd-124">IHostControl Interface</span></span>](ihostcontrol-interface.md)
- [<span data-ttu-id="18fcd-125">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="18fcd-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
