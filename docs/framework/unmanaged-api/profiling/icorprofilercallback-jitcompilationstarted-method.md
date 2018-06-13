---
title: ICorProfilerCallback::JITCompilationStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCompilationStarted
helpviewer_keywords:
- JITCompilationStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCompilationStarted method [.NET Framework profiling]
ms.assetid: 31782b36-d311-4518-8f45-25f65385af5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fa1081afc77c8116d8858c187401555409b4dcd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453978"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="fda28-102">ICorProfilerCallback::JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="fda28-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="fda28-103">Upozorní profileru, že kompilátoru za běhu (JIT) byla spuštěna zkompilovat funkce.</span><span class="sxs-lookup"><span data-stu-id="fda28-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fda28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fda28-104">Syntax</span></span>  
  
```  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fda28-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fda28-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="fda28-106">[v] ID funkce, pro který se spouští kompilace.</span><span class="sxs-lookup"><span data-stu-id="fda28-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="fda28-107">[v] Hodnotu, která určuje profileru, zda blokování ovlivní operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="fda28-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="fda28-108">Hodnota je `true` Pokud blokování může způsobit počkejte volající vlákno k návratu z této zpětného volání; modulu runtime, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="fda28-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="fda28-109">I když hodnota `true` nebude poškodit modul runtime, zkreslit profilování výsledky.</span><span class="sxs-lookup"><span data-stu-id="fda28-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fda28-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fda28-110">Remarks</span></span>  
 <span data-ttu-id="fda28-111">Je možné získat více než jednu dvojici `JITCompilationStarted` a [icorprofilercallback::jitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) volání pro každou funkci kvůli způsobu, jakým modul runtime konstruktory třídu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="fda28-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="fda28-112">Například metoda JIT – kompilace A začne modul runtime, ale konstruktoru třídy pro třídy B musí být spuštěn.</span><span class="sxs-lookup"><span data-stu-id="fda28-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="fda28-113">Proto runtime JIT zkompiluje v konstruktoru pro třídy B a spustí ho.</span><span class="sxs-lookup"><span data-stu-id="fda28-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="fda28-114">Je spuštěn v konstruktoru, provede volání do metody A, což způsobí, že metoda A Chcete-li být kompilována znovu.</span><span class="sxs-lookup"><span data-stu-id="fda28-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="fda28-115">V tomto scénáři se zastavilo první JIT – kompilace metody A.</span><span class="sxs-lookup"><span data-stu-id="fda28-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="fda28-116">Však obě pokusy o metoda JIT – kompilace A oznamuje s událostmi JIT – kompilace.</span><span class="sxs-lookup"><span data-stu-id="fda28-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="fda28-117">Pokud budete profileru nahraďte kód Microsoft (MSIL intermediate language) pro metodu A voláním [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metodu, musíte udělat, tak pro obě `JITCompilationStarted` události, ale může používat stejný blok MSIL pro obě.</span><span class="sxs-lookup"><span data-stu-id="fda28-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="fda28-118">Profilery musí podporovat posloupnost zpětných volání JIT v případech, kde jsou dva vláken současně provádění zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="fda28-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="fda28-119">Například přístup z více vláken A volá `JITCompilationStarted`.</span><span class="sxs-lookup"><span data-stu-id="fda28-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="fda28-120">Nicméně před volání vláken A `JITCompilationFinished`, vlákno B volání [icorprofilercallback::exceptionsearchfunctionenter –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z vlákna na `JITCompilationStarted` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="fda28-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="fda28-121">Může se zdát, že funkce ID nesmí být ještě platný protože volání `JITCompilationFinished` kdyby ještě přijatý nástrojem profileru.</span><span class="sxs-lookup"><span data-stu-id="fda28-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="fda28-122">V případě tohoto typu, je však platné ID funkce.</span><span class="sxs-lookup"><span data-stu-id="fda28-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fda28-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fda28-123">Requirements</span></span>  
 <span data-ttu-id="fda28-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fda28-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fda28-125">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fda28-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fda28-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fda28-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fda28-127">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fda28-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fda28-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="fda28-128">See Also</span></span>  
 [<span data-ttu-id="fda28-129">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fda28-129">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="fda28-130">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="fda28-130">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
