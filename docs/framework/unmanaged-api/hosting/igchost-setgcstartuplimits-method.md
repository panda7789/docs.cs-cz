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
ms.openlocfilehash: e65a83d1da0580436babd15e4f27e2db7a698668
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377602"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="680a7-102">IGCHost::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="680a7-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="680a7-103">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="680a7-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="680a7-104">Od verze rozhraní .NET Framework 4.5, můžete nastavit velikost segmentu a maximální 0. generace, velikost na hodnoty vyšší než `DWORD` pomocí [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="680a7-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="680a7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="680a7-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="680a7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="680a7-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="680a7-107">[in] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="680a7-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="680a7-108">[in] Maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="680a7-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="680a7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="680a7-109">Remarks</span></span>  
 <span data-ttu-id="680a7-110">`SetGCStartupLimits` Metoda může být volána pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="680a7-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="680a7-111">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="680a7-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="680a7-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="680a7-112">Requirements</span></span>  
 <span data-ttu-id="680a7-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="680a7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="680a7-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="680a7-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="680a7-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="680a7-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="680a7-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="680a7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680a7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="680a7-117">See also</span></span>

- [<span data-ttu-id="680a7-118">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="680a7-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
