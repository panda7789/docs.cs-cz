---
title: ICorProfilerCallback::JITFunctionPitched – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITFunctionPitched
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITFunctionPitched
helpviewer_keywords:
- JITFunctionPitched method [.NET Framework profiling]
- ICorProfilerCallback::JITFunctionPitched method [.NET Framework profiling]
ms.assetid: 116085df-7a77-404a-afac-d0557a12b986
topic_type:
- apiref
ms.openlocfilehash: cda629b7a6560ca5d731cd88cffc2cffd3486d8a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866209"
---
# <a name="icorprofilercallbackjitfunctionpitched-method"></a><span data-ttu-id="cdf44-102">ICorProfilerCallback::JITFunctionPitched – metoda</span><span class="sxs-lookup"><span data-stu-id="cdf44-102">ICorProfilerCallback::JITFunctionPitched Method</span></span>
<span data-ttu-id="cdf44-103">Upozorní profileru, že byla z paměti odebrána funkce, která byla zkompilována za běhu (JIT).</span><span class="sxs-lookup"><span data-stu-id="cdf44-103">Notifies the profiler that a function that has been just-in-time (JIT)-compiled has been removed from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdf44-104">Syntax</span></span>  
  
```cpp  
HRESULT JITFunctionPitched(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdf44-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdf44-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cdf44-106">pro ID odebrané funkce</span><span class="sxs-lookup"><span data-stu-id="cdf44-106">[in] The ID of the function that was removed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdf44-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdf44-107">Remarks</span></span>  
 <span data-ttu-id="cdf44-108">Pokud je zavolána funkce odebrané, Profiler obdrží nové události kompilace JIT, když je funkce znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="cdf44-108">If the removed function is called, the profiler will receive new JIT-compilation events when the function is recompiled.</span></span> <span data-ttu-id="cdf44-109">Kompilátor JIT (Common Language Runtime) v současné době neodebere funkce z paměti, takže toto zpětné volání se v tuto chvíli nepoužívá a profil nebude přijímat.</span><span class="sxs-lookup"><span data-stu-id="cdf44-109">Currently, the common language runtime (CLR) JIT compiler does not remove functions from memory, so this callback is currently not used and will not be received by the profiler.</span></span>  
  
 <span data-ttu-id="cdf44-110">Hodnota `functionId` není platná, dokud nebude funkce znovu zkompilována.</span><span class="sxs-lookup"><span data-stu-id="cdf44-110">The value of `functionId` is not valid until the function is recompiled.</span></span> <span data-ttu-id="cdf44-111">Když je funkce znovu zkompilována, bude použita stejná hodnota `functionId`.</span><span class="sxs-lookup"><span data-stu-id="cdf44-111">When the function is recompiled, the same `functionId` value will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdf44-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdf44-112">Requirements</span></span>  
 <span data-ttu-id="cdf44-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdf44-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdf44-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cdf44-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cdf44-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cdf44-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdf44-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdf44-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf44-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdf44-117">See also</span></span>

- [<span data-ttu-id="cdf44-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cdf44-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
