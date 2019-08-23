---
title: IGCHost2 – rozhraní
ms.date: 03/30/2017
api_name:
- IGCHost2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2
helpviewer_keywords:
- IGCHost2 interface [.NET Framework hosting]
ms.assetid: e5323fa4-18ac-424d-859d-a65a550d08d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21ce9cbd007858c0f39e12622eff819154ab83f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928620"
---
# <a name="igchost2-interface"></a><span data-ttu-id="12f73-102">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12f73-102">IGCHost2 Interface</span></span>
<span data-ttu-id="12f73-103">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="12f73-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12f73-104">Pro nové vývojové prostředí doporučujeme místo toho použít rozhraní [ICLRGCManager2 –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="12f73-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12f73-105">Metody</span><span class="sxs-lookup"><span data-stu-id="12f73-105">Methods</span></span>  
  
|<span data-ttu-id="12f73-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="12f73-106">Method</span></span>|<span data-ttu-id="12f73-107">Popis</span><span class="sxs-lookup"><span data-stu-id="12f73-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12f73-108">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="12f73-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="12f73-109">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="12f73-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="12f73-110">Povoluje generaci 0 a velikosti segmentů větší `DWORD`než.</span><span class="sxs-lookup"><span data-stu-id="12f73-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="12f73-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f73-111">Requirements</span></span>  
 <span data-ttu-id="12f73-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f73-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f73-113">**Hlaviček** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="12f73-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="12f73-114">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="12f73-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12f73-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f73-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12f73-116">See also</span></span>

- [<span data-ttu-id="12f73-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="12f73-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="12f73-118">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="12f73-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="12f73-119">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="12f73-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
