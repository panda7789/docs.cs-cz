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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1abc4dd209581c9f7c8e950ea1addc74c611d248
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226055"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="7f330-102">ICorProfilerCallback::JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="7f330-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="7f330-103">Oznámí profileru, že byla dokončena kompilátor just-in-time (JIT) kompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="7f330-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f330-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f330-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f330-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f330-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7f330-106">[in] ID funkce, která byla zkompilována.</span><span class="sxs-lookup"><span data-stu-id="7f330-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="7f330-107">[in] Hodnota označující, zda kompilace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="7f330-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="7f330-108">[in] Hodnotu, která k profileru, zda blokování bude mít vliv na operace modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7f330-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="7f330-109">Hodnota je `true` Pokud blokování může způsobit, že modul runtime počká pro volajícího vlákna má vrátit z této zpětné volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="7f330-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="7f330-110">I když hodnota `true` nepoškodí modul runtime, je zkosení výsledků profilace.</span><span class="sxs-lookup"><span data-stu-id="7f330-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f330-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f330-111">Requirements</span></span>  
 <span data-ttu-id="7f330-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f330-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f330-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f330-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f330-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f330-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7f330-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7f330-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7f330-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f330-116">See also</span></span>

- [<span data-ttu-id="7f330-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f330-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7f330-118">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="7f330-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
