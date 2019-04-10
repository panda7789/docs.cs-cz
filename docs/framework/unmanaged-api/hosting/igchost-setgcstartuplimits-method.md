---
title: IGCHost::SetGCStartupLimits – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 365261883f0b81884bb7cf70614628c05f9067c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221004"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="56cb6-102">IGCHost::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="56cb6-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="56cb6-103">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="56cb6-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="56cb6-104">Počínaje [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], můžete nastavit velikost segmentu a hodnoty větší než maximální generace 0 velikost `DWORD` pomocí [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="56cb6-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56cb6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56cb6-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56cb6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="56cb6-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="56cb6-107">[in] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="56cb6-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="56cb6-108">[in] Maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="56cb6-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56cb6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56cb6-109">Remarks</span></span>  
 <span data-ttu-id="56cb6-110">`SetGCStartupLimits` Metoda může být volána pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="56cb6-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="56cb6-111">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="56cb6-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56cb6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56cb6-112">Requirements</span></span>  
 <span data-ttu-id="56cb6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56cb6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56cb6-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="56cb6-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="56cb6-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="56cb6-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="56cb6-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="56cb6-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56cb6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56cb6-117">See also</span></span>

- [<span data-ttu-id="56cb6-118">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56cb6-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
