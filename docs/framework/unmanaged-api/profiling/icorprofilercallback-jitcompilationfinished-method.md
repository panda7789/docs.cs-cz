---
title: "ICorProfilerCallback::JITCompilationFinished – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCompilationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCompilationFinished
helpviewer_keywords:
- JITCompilationFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationFinished method [.NET Framework profiling]
ms.assetid: 8dcd7537-d0c6-498c-8a56-2c060310ef65
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9bd1a163fa5e941c68c5dd8d7d3221e8a5aa3df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcompilationfinished-method"></a><span data-ttu-id="abe17-102">ICorProfilerCallback::JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="abe17-102">ICorProfilerCallback::JITCompilationFinished Method</span></span>
<span data-ttu-id="abe17-103">Upozorní profileru, že kompilování funkce kompilátoru za běhu (JIT) byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="abe17-103">Notifies the profiler that the just-in-time (JIT) compiler has finished compiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe17-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abe17-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationFinished(  
    [in] FunctionID functionId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abe17-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="abe17-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="abe17-106">[v] ID funkce, která byla zkompilovat.</span><span class="sxs-lookup"><span data-stu-id="abe17-106">[in] The ID of the function that was compiled.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="abe17-107">[v] Hodnota, která určuje, zda kompilace byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="abe17-107">[in] A value indicating whether compilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="abe17-108">[v] Hodnotu, která určuje profileru, zda blokování ovlivní operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abe17-108">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="abe17-109">Hodnota je `true` Pokud blokování může způsobit počkejte volající vlákno k návratu z této zpětného volání; modulu runtime, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="abe17-109">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="abe17-110">I když hodnota `true` nebude poškodit modul runtime, zkreslit profilování výsledky.</span><span class="sxs-lookup"><span data-stu-id="abe17-110">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe17-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abe17-111">Requirements</span></span>  
 <span data-ttu-id="abe17-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abe17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe17-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="abe17-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="abe17-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe17-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe17-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe17-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="abe17-116">See Also</span></span>  
 [<span data-ttu-id="abe17-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abe17-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="abe17-118">JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="abe17-118">JITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
