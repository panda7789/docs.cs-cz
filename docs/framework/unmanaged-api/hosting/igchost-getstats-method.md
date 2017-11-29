---
title: "IGCHost::GetStats – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c8db4f854b73d04e7260457c978a7a644677559
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="e97f3-102">IGCHost::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="e97f3-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="e97f3-103">Získá statistiku pro aktuální stav kolekce systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e97f3-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e97f3-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e97f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e97f3-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="e97f3-106">[ve out] Ukazatel [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura, která obsahuje statistiku pro aktuální stav kolekce systém uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e97f3-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e97f3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e97f3-107">Remarks</span></span>  
 <span data-ttu-id="e97f3-108">Statistiku lze inteligentní přidělení systému pomohou systém kolekce paměti fungovat.</span><span class="sxs-lookup"><span data-stu-id="e97f3-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="e97f3-109">Například přidělení systém může určit, po kontrole statistiky, které je nutné přidat více paměti nebo vynutit kolekce.</span><span class="sxs-lookup"><span data-stu-id="e97f3-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e97f3-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e97f3-110">Requirements</span></span>  
 <span data-ttu-id="e97f3-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e97f3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e97f3-112">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="e97f3-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e97f3-113">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e97f3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e97f3-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e97f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e97f3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e97f3-115">See Also</span></span>  
 [<span data-ttu-id="e97f3-116">Igchost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e97f3-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
