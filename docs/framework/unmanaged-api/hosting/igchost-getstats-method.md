---
title: IGCHost::GetStats – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c3e0d6f68ffa5280d4616d4fa4ac60b4cb86f6a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437762"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="95576-102">IGCHost::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="95576-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="95576-103">Získá statistiku pro aktuální stav kolekce systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="95576-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95576-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95576-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="95576-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="95576-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="95576-106">[ve out] Ukazatel [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura, která obsahuje statistiku pro aktuální stav kolekce systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="95576-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95576-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95576-107">Remarks</span></span>  
 <span data-ttu-id="95576-108">Statistiku lze inteligentní přidělení systému pomohou systém kolekce paměti fungovat.</span><span class="sxs-lookup"><span data-stu-id="95576-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="95576-109">Například přidělení systém může určit, po kontrole statistiky, které je nutné přidat více paměti nebo vynutit kolekce.</span><span class="sxs-lookup"><span data-stu-id="95576-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95576-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95576-110">Requirements</span></span>  
 <span data-ttu-id="95576-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95576-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95576-112">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="95576-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="95576-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95576-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95576-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95576-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95576-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="95576-115">See Also</span></span>  
 [<span data-ttu-id="95576-116">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="95576-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
