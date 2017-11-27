---
title: "ICorProfilerInfo::ForceGC – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.ForceGC
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3a3389c6675e992c362e3e0a77dfbc97e142ef8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="eccaa-102">ICorProfilerInfo::ForceGC – metoda</span><span class="sxs-lookup"><span data-stu-id="eccaa-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="eccaa-103">Vynutí uvolňování paměti v rámci common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="eccaa-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eccaa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eccaa-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="eccaa-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eccaa-105">Remarks</span></span>  
 <span data-ttu-id="eccaa-106">`ForceGC` Metoda musí být volána pouze z vlákna, který má nebude nikdy spuštěn spravovaného kódu a nemá žádné profileru zpětná volání v jeho zásobníku.</span><span class="sxs-lookup"><span data-stu-id="eccaa-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="eccaa-107">Je nejvhodnější implementace vytvořit samostatné vlákno v rámci profileru, který volá `ForceGC` při signál.</span><span class="sxs-lookup"><span data-stu-id="eccaa-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eccaa-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eccaa-108">Requirements</span></span>  
 <span data-ttu-id="eccaa-109">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eccaa-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eccaa-110">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eccaa-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eccaa-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eccaa-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eccaa-112">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eccaa-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eccaa-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="eccaa-113">See Also</span></span>  
 [<span data-ttu-id="eccaa-114">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eccaa-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
