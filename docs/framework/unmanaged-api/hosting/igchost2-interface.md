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
ms.openlocfilehash: 75bef91eb70c8109653741452362cd2e85f625ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138135"
---
# <a name="igchost2-interface"></a><span data-ttu-id="6e5f2-102">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5f2-102">IGCHost2 Interface</span></span>
<span data-ttu-id="6e5f2-103">Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e5f2-104">Pro nový vývoj doporučujeme použít [iclrgcmanager2 –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) místo toho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-104">For new development, we recommend that you use the [ICLRGCManager2](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md) interface instead.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e5f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6e5f2-105">Methods</span></span>  
  
|<span data-ttu-id="6e5f2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e5f2-106">Method</span></span>|<span data-ttu-id="6e5f2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6e5f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e5f2-108">SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="6e5f2-108">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)|<span data-ttu-id="6e5f2-109">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-109">Sets the segment size and the maximum size for generation 0.</span></span> <span data-ttu-id="6e5f2-110">Umožňuje 0. generace a větší velikosti segmentů `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="6e5f2-110">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e5f2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e5f2-111">Requirements</span></span>  
 <span data-ttu-id="6e5f2-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e5f2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5f2-113">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="6e5f2-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6e5f2-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6e5f2-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e5f2-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e5f2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5f2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e5f2-116">See also</span></span>

- [<span data-ttu-id="6e5f2-117">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6e5f2-117">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="6e5f2-118">Rozhraní pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="6e5f2-118">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="6e5f2-119">CorRuntimeHost – třída typu coclass</span><span class="sxs-lookup"><span data-stu-id="6e5f2-119">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
