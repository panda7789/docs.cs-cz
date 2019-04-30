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
ms.openlocfilehash: 88f86385ba4f4186d14994a2028ee11c42127546
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927246"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="f5be0-102">IGCHost::GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="f5be0-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="f5be0-103">Získá statistiku vlákno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="f5be0-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5be0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5be0-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5be0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5be0-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="f5be0-106">[in] Ukazatel na soubor cookie fiber, který určuje vlákna, pro které se mají načíst statistiky.</span><span class="sxs-lookup"><span data-stu-id="f5be0-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="f5be0-107">[out v] Ukazatel [cor_gc_thread_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) strukturu, která obsahuje statistiku kolekce uvolnění paměti pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="f5be0-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5be0-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5be0-108">Requirements</span></span>  
 <span data-ttu-id="f5be0-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5be0-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5be0-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f5be0-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f5be0-111">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5be0-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5be0-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5be0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5be0-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5be0-113">See also</span></span>

- [<span data-ttu-id="f5be0-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5be0-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
