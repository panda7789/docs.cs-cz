---
title: ICorProfilerCallback::JITCompilationFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type:
- apiref
ms.openlocfilehash: 0da67f0d4be779cc21481d03a21209620289888e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500052"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="10006-102">ICorProfilerCallback::JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="10006-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="10006-103">Upozorní profileru, že kompilátor JIT (just-in-time) dokončil kompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="10006-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10006-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10006-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10006-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10006-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="10006-106">\[v] ID funkce, která byla zkompilována.</span><span class="sxs-lookup"><span data-stu-id="10006-106">\[in] The ID of the function that was compiled.</span></span>

- `hrStatus`

  <span data-ttu-id="10006-107">\[in] hodnota označující, zda byla kompilace úspěšná.</span><span class="sxs-lookup"><span data-stu-id="10006-107">\[in] A value indicating whether compilation was successful.</span></span>

- `fIsSafeToBlock`

  <span data-ttu-id="10006-108">\[in] hodnota, která označuje Profiler, zda bude blokování ovlivněno operací modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="10006-108">\[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="10006-109">Hodnota je, `true` Pokud blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání. v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="10006-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>

  <span data-ttu-id="10006-110">I když hodnota `true` nebude mít vliv na modul runtime, může zkosit výsledky profilace.</span><span class="sxs-lookup"><span data-stu-id="10006-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>

## <a name="requirements"></a><span data-ttu-id="10006-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10006-111">Requirements</span></span>  
 <span data-ttu-id="10006-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10006-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10006-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="10006-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="10006-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="10006-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10006-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10006-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10006-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10006-116">See also</span></span>

- [<span data-ttu-id="10006-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10006-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="10006-118">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="10006-118">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
