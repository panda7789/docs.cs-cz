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
ms.openlocfilehash: e1fe38419cda328c919f0840d51cf6336919aa60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864190"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="bd648-102">ICorProfilerInfo::ForceGC – metoda</span><span class="sxs-lookup"><span data-stu-id="bd648-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="bd648-103">Vynutí uvolňování paměti v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="bd648-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd648-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd648-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd648-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd648-105">Remarks</span></span>  
 <span data-ttu-id="bd648-106">Metoda `ForceGC` musí být volána pouze z vlákna, které nikdy nespouštělo spravovaný kód a nemá v zásobníku žádná zpětná volání profileru.</span><span class="sxs-lookup"><span data-stu-id="bd648-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="bd648-107">Nejpohodlnější implementace je vytvořit samostatné vlákno v rámci profileru, který při signalizaci zavolá `ForceGC`.</span><span class="sxs-lookup"><span data-stu-id="bd648-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd648-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bd648-108">Requirements</span></span>  
 <span data-ttu-id="bd648-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd648-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd648-110">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bd648-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd648-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bd648-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd648-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd648-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd648-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd648-113">See also</span></span>

- [<span data-ttu-id="bd648-114">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bd648-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
