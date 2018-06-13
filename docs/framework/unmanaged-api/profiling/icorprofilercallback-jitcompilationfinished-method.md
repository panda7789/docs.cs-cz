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
ms.openlocfilehash: dbf447e1325b4acaa26c9bb16d7d1a736eb20a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453548"
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="3f1da-102">ICorProfilerCallback::JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="3f1da-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="3f1da-103">Upozorní profileru, že kompilování funkce kompilátoru za běhu (JIT) byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="3f1da-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f1da-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3f1da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f1da-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3f1da-106">[v] ID funkce, která byla zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="3f1da-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3f1da-107">[v] Hodnota, která určuje, zda kompilace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="3f1da-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="3f1da-108">[v] Hodnotu, která určuje profileru, zda blokování ovlivní operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="3f1da-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="3f1da-109">Hodnota je `true` Pokud blokování může způsobit počkejte volající vlákno k návratu z této zpětného volání; modulu runtime, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="3f1da-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="3f1da-110">I když hodnota `true` nebude poškodit modul runtime, zkreslit profilování výsledky.</span><span class="sxs-lookup"><span data-stu-id="3f1da-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f1da-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f1da-111">Requirements</span></span>  
 <span data-ttu-id="3f1da-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f1da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f1da-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f1da-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f1da-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f1da-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f1da-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f1da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1da-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f1da-116">See Also</span></span>  
 [<span data-ttu-id="3f1da-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3f1da-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="3f1da-118">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="3f1da-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
