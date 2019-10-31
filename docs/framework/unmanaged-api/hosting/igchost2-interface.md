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
ms.openlocfilehash: 43c16415c91521194e0d88be84dd176c3fdadad1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134839"
---
# <a name="igchost2-interface"></a><span data-ttu-id="ee2b8-102">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee2b8-102">IGCHost2 Interface</span></span>
<span data-ttu-id="ee2b8-103">Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ee2b8-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee2b8-104">Pro nové vývojové prostředí doporučujeme místo toho použít rozhraní [ICLRGCManager2 –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ee2b8-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee2b8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ee2b8-105">Methods</span></span>  
  
|<span data-ttu-id="ee2b8-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee2b8-106">Method</span></span>|<span data-ttu-id="ee2b8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ee2b8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee2b8-108">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="ee2b8-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="ee2b8-109">Nastaví velikost segmentu a maximální velikost pro generaci 0.</span><span class="sxs-lookup"><span data-stu-id="ee2b8-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="ee2b8-110">Povoluje generaci 0 a velikosti segmentů větší než `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="ee2b8-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ee2b8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ee2b8-111">Requirements</span></span>  
 <span data-ttu-id="ee2b8-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee2b8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee2b8-113">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="ee2b8-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ee2b8-114">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ee2b8-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee2b8-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee2b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2b8-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee2b8-116">See also</span></span>

- [<span data-ttu-id="ee2b8-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="ee2b8-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ee2b8-118">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="ee2b8-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="ee2b8-119">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="ee2b8-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
