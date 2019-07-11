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
ms.openlocfilehash: c9104550438a2a066cdf052b8d6592e86b831194
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749995"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="70238-102">IGCHost::SetGCStartupLimits – metoda</span><span class="sxs-lookup"><span data-stu-id="70238-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="70238-103">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="70238-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70238-104">Od verze rozhraní .NET Framework 4.5, můžete nastavit velikost segmentu a maximální 0. generace, velikost na hodnoty vyšší než `DWORD` pomocí [igchost2::setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="70238-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70238-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70238-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70238-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="70238-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="70238-107">[in] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="70238-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="70238-108">[in] Maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="70238-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70238-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70238-109">Remarks</span></span>  
 <span data-ttu-id="70238-110">`SetGCStartupLimits` Metoda může být volána pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="70238-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="70238-111">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="70238-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70238-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70238-112">Requirements</span></span>  
 <span data-ttu-id="70238-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70238-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70238-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="70238-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="70238-115">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70238-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70238-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70238-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70238-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70238-117">See also</span></span>

- [<span data-ttu-id="70238-118">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70238-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
