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
ms.openlocfilehash: 4a7a2da58e197749d492f24c7a12134508efef57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805224"
---
# <a name="igchostgetthreadstats-method"></a><span data-ttu-id="c4461-102">IGCHost::GetThreadStats – metoda</span><span class="sxs-lookup"><span data-stu-id="c4461-102">IGCHost::GetThreadStats Method</span></span>
<span data-ttu-id="c4461-103">Načte statistiku jednotlivých vláken pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c4461-103">Gets the per-thread statistics for garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4461-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4461-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStats (  
    [in] DWORD *pFiberCookie,  
    [in, out] COR_GC_THREAD_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4461-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4461-105">Parameters</span></span>  
 `pFiberCookie`  
 <span data-ttu-id="c4461-106">pro Ukazatel na vláknový soubor cookie, který určuje vlákno, pro které chcete získat statistiku.</span><span class="sxs-lookup"><span data-stu-id="c4461-106">[in] A pointer to a fiber cookie that specifies the thread for which to retrieve the statistics.</span></span>  
  
 `pStats`  
 <span data-ttu-id="c4461-107">[in, out] Ukazatel na strukturu [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) , která obsahuje statistiku uvolňování paměti pro zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="c4461-107">[in, out] A pointer to a [COR_GC_THREAD_STATS](cor-gc-thread-stats-structure.md) structure that contains the garbage collection statistics for the specified thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4461-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4461-108">Requirements</span></span>  
 <span data-ttu-id="c4461-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4461-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4461-110">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="c4461-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c4461-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c4461-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4461-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4461-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4461-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4461-113">See also</span></span>

- [<span data-ttu-id="c4461-114">IGCHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4461-114">IGCHost Interface</span></span>](igchost-interface.md)
