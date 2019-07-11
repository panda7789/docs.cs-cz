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
ms.openlocfilehash: 3e374c03ca90c904cd4ef8a4585cb35ccf43cb43
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766524"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="b440f-102">IGCHost::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="b440f-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="b440f-103">Získá statistiku pro aktuální stav systému uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="b440f-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b440f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b440f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b440f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b440f-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="b440f-106">[out v] Ukazatel [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) strukturu, která obsahuje statistiku pro aktuální stav systému uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="b440f-106">[in, out] A pointer to a [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b440f-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b440f-107">Remarks</span></span>  
 <span data-ttu-id="b440f-108">Statistiku lze inteligentní přidělení systému systém uvolňování paměti kolekce, provoz.</span><span class="sxs-lookup"><span data-stu-id="b440f-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="b440f-109">Například přidělení systém může určit, prohlédněte si statistiky, které je nutné přidat další paměť nebo vynutit kolekce.</span><span class="sxs-lookup"><span data-stu-id="b440f-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b440f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b440f-110">Requirements</span></span>  
 <span data-ttu-id="b440f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b440f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b440f-112">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="b440f-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="b440f-113">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b440f-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b440f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b440f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b440f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b440f-115">See also</span></span>

- [<span data-ttu-id="b440f-116">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b440f-116">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
