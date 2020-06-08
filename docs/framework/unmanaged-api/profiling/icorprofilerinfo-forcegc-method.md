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
ms.openlocfilehash: 9bc6619f3ef383c7bf60a310a87f056cfc43cddf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84498671"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="41ec9-102">ICorProfilerInfo::ForceGC – metoda</span><span class="sxs-lookup"><span data-stu-id="41ec9-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="41ec9-103">Vynutí uvolňování paměti v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="41ec9-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41ec9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41ec9-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="41ec9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41ec9-105">Remarks</span></span>  
 <span data-ttu-id="41ec9-106">`ForceGC`Metoda musí být volána pouze z vlákna, které nikdy nespouštělo spravovaný kód a nemá v zásobníku žádná zpětná volání profileru.</span><span class="sxs-lookup"><span data-stu-id="41ec9-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="41ec9-107">Nejpohodlnější implementace je vytvořit samostatné vlákno v rámci profileru, který volá `ForceGC` při signalizaci.</span><span class="sxs-lookup"><span data-stu-id="41ec9-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41ec9-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="41ec9-108">Requirements</span></span>  
 <span data-ttu-id="41ec9-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41ec9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41ec9-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="41ec9-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41ec9-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41ec9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41ec9-112">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41ec9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41ec9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41ec9-113">See also</span></span>

- [<span data-ttu-id="41ec9-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="41ec9-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
