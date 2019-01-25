---
title: IGCHost::GetThreadStats – metoda
ms.date: 03/30/2017
api_name:
- IGCHost.GetThreadStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetThreadStats
helpviewer_keywords:
- IGCHost::GetThreadStats method [.NET Framework hosting]
- GetThreadStats method [.NET Framework hosting]
ms.assetid: 826baa9b-9218-4736-a509-7ab193b125a0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c3d71c75527daa9a9c130d5aaa0d6838816c276
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559421"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="e3120-102">IGCHost::GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="e3120-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="e3120-103">Získá statistiku vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e3120-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3120-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3120-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3120-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3120-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="e3120-106">[in] Ukazatel na soubor cookie fiber, který určuje vlákna, pro které se mají načíst statistiky.</span><span class="sxs-lookup"><span data-stu-id="e3120-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="e3120-107">[out v] Ukazatel [cor_gc_thread_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) strukturu, která obsahuje statistiku kolekce uvolnění paměti pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="e3120-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3120-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3120-108">Requirements</span></span>  
 <span data-ttu-id="e3120-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3120-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3120-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="e3120-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="e3120-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e3120-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e3120-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3120-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3120-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3120-113">See also</span></span>
- [<span data-ttu-id="e3120-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e3120-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
