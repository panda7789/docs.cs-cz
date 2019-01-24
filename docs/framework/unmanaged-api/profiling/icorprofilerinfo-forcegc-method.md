---
title: ICorProfilerInfo::ForceGC – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c30a666dcbac553d05cc5f54d5dbb326eb6a10e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706693"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="76fc1-102">ICorProfilerInfo::ForceGC – metoda</span><span class="sxs-lookup"><span data-stu-id="76fc1-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="76fc1-103">Vynutí uvolňování paměti dochází v rámci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="76fc1-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76fc1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76fc1-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="76fc1-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76fc1-105">Remarks</span></span>  
 <span data-ttu-id="76fc1-106">`ForceGC` Metoda musí být volána pouze z vlákna, které dosud nespustil spravovaný kód a nemá žádné zpětná volání profileru pro svůj zásobník.</span><span class="sxs-lookup"><span data-stu-id="76fc1-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="76fc1-107">Nejpohodlnější implementace je vytvoření samostatného vlákna v profileru, který volá `ForceGC` při signál.</span><span class="sxs-lookup"><span data-stu-id="76fc1-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76fc1-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76fc1-108">Requirements</span></span>  
 <span data-ttu-id="76fc1-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76fc1-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76fc1-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="76fc1-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76fc1-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76fc1-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76fc1-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76fc1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76fc1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76fc1-113">See also</span></span>
- [<span data-ttu-id="76fc1-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76fc1-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
