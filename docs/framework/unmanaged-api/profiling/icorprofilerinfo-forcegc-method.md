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
ms.openlocfilehash: 5672d1b89b4260d1ebfbf444deb2702f215a0e95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078080"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="eb49b-102">ICorProfilerInfo::ForceGC – metoda</span><span class="sxs-lookup"><span data-stu-id="eb49b-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="eb49b-103">Vynutí uvolňování paměti dochází v rámci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="eb49b-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb49b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb49b-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="eb49b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb49b-105">Remarks</span></span>  
 <span data-ttu-id="eb49b-106">`ForceGC` Metoda musí být volána pouze z vlákna, které dosud nespustil spravovaný kód a nemá žádné zpětná volání profileru pro svůj zásobník.</span><span class="sxs-lookup"><span data-stu-id="eb49b-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="eb49b-107">Nejpohodlnější implementace je vytvoření samostatného vlákna v profileru, který volá `ForceGC` při signál.</span><span class="sxs-lookup"><span data-stu-id="eb49b-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb49b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb49b-108">Requirements</span></span>  
 <span data-ttu-id="eb49b-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb49b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb49b-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb49b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb49b-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb49b-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="eb49b-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="eb49b-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="eb49b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb49b-113">See also</span></span>

- [<span data-ttu-id="eb49b-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb49b-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
