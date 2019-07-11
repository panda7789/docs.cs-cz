---
title: IGCHost2::SetGCStartupLimitsEx – metoda
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e834042c5e00709fcb2198c1496a8a630841d069
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779542"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="fefea-102">IGCHost2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="fefea-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="fefea-103">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="fefea-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fefea-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fefea-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fefea-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fefea-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="fefea-106">[in] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="fefea-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="fefea-107">[in] Maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="fefea-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fefea-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fefea-108">Remarks</span></span>  
 <span data-ttu-id="fefea-109">Hodnoty, které `SetGCStartupLimitsEx` sady se dá nastavit pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="fefea-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="fefea-110">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="fefea-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fefea-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fefea-111">Requirements</span></span>  
 <span data-ttu-id="fefea-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fefea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fefea-113">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="fefea-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="fefea-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fefea-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fefea-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fefea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fefea-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fefea-116">See also</span></span>

- [<span data-ttu-id="fefea-117">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fefea-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
