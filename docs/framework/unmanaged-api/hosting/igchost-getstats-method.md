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
ms.openlocfilehash: 67668aa7ff9faf035a047e485a8a3c8a451f45b9
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805240"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="835a9-102">IGCHost::GetStats – metoda</span><span class="sxs-lookup"><span data-stu-id="835a9-102">IGCHost::GetStats Method</span></span>
<span data-ttu-id="835a9-103">Získá statistiku pro aktuální stav systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="835a9-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="835a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="835a9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="835a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="835a9-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="835a9-106">[in, out] Ukazatel na strukturu [COR_GC_STATS](cor-gc-stats-structure.md) , která obsahuje statistiku pro aktuální stav systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="835a9-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="835a9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="835a9-107">Remarks</span></span>  
 <span data-ttu-id="835a9-108">Statistiku může používat systém inteligentního přidělování dat, aby mohl systém uvolňování paměti pracovat.</span><span class="sxs-lookup"><span data-stu-id="835a9-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="835a9-109">Systém přidělení může například určit, že po kontrole statistiky bude nutné přidat více paměti nebo vynutit kolekci.</span><span class="sxs-lookup"><span data-stu-id="835a9-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="835a9-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="835a9-110">Requirements</span></span>  
 <span data-ttu-id="835a9-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="835a9-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="835a9-112">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="835a9-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="835a9-113">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="835a9-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="835a9-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="835a9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="835a9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="835a9-115">See also</span></span>

- [<span data-ttu-id="835a9-116">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="835a9-116">IGCHost Interface</span></span>](igchost-interface.md)
