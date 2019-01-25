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
ms.openlocfilehash: f61f6ed5712f3c98f06f5fa76657f3fa7b70fe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666329"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="3390e-102">IGCHost2::SetGCStartupLimitsEx – metoda</span><span class="sxs-lookup"><span data-stu-id="3390e-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="3390e-103">Nastaví velikost segmentu a maximální velikost pro 0. generace.</span><span class="sxs-lookup"><span data-stu-id="3390e-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3390e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3390e-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3390e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3390e-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="3390e-106">[in] Velikost segmentu používá systém uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="3390e-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="3390e-107">[in] Maximální velikost 0. generace.</span><span class="sxs-lookup"><span data-stu-id="3390e-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3390e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3390e-108">Remarks</span></span>  
 <span data-ttu-id="3390e-109">Hodnoty, které `SetGCStartupLimitsEx` sady se dá nastavit pouze před spuštěním hostitele.</span><span class="sxs-lookup"><span data-stu-id="3390e-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="3390e-110">Tyto hodnoty není možné později změnit.</span><span class="sxs-lookup"><span data-stu-id="3390e-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3390e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3390e-111">Requirements</span></span>  
 <span data-ttu-id="3390e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3390e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3390e-113">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="3390e-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="3390e-114">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3390e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3390e-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3390e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3390e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3390e-116">See also</span></span>
- [<span data-ttu-id="3390e-117">IGCHost2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3390e-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
