---
title: "IGCHost::GetThreadStats – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe84dd4d231bacba6792836844058b7256124db5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="25137-102">IGCHost::GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="25137-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="25137-103">Získá statistiku objektů vlákno pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="25137-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25137-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25137-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25137-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25137-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="25137-106">[v] Ukazatel na fiber souboru cookie, který určuje vlákno, pro které chcete získat statistiku.</span><span class="sxs-lookup"><span data-stu-id="25137-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="25137-107">[ve out] Ukazatel [cor_gc_thread_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) struktura, která obsahuje statistiku kolekce uvolňování paměti pro zadanou vlákno.</span><span class="sxs-lookup"><span data-stu-id="25137-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25137-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25137-108">Requirements</span></span>  
 <span data-ttu-id="25137-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25137-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25137-110">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="25137-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="25137-111">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25137-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25137-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25137-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25137-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="25137-113">See Also</span></span>  
 [<span data-ttu-id="25137-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25137-114">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
