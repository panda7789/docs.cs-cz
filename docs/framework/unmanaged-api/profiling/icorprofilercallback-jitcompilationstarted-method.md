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
ms.openlocfilehash: 57981ef134dc3f30337d47f5cee426a25d0414cf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500036"
---
# <a name="icorprofilercallbackjitcompilationstarted-method"></a><span data-ttu-id="0aa4c-102">ICorProfilerCallback::JITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="0aa4c-102">ICorProfilerCallback::JITCompilationStarted Method</span></span>
<span data-ttu-id="0aa4c-103">Upozorní profileru, že kompilátor JIT (just-in-time) začal kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-103">Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa4c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0aa4c-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCompilationStarted(  
    [in] FunctionID functionId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0aa4c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0aa4c-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="0aa4c-106">pro ID funkce, pro kterou je kompilace spouštěna.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-106">[in] The ID of the function for which the compilation is starting.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="0aa4c-107">pro Hodnota, která označuje Profiler, zda blokování bude mít vliv na operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-107">[in] A value indicating to the profiler whether blocking will affect the operation of the runtime.</span></span> <span data-ttu-id="0aa4c-108">Hodnota je, `true` Pokud blokování může způsobit, že modul runtime počká, než se volající vlákno vrátí z tohoto zpětného volání. v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="0aa4c-108">The value is `true` if blocking may cause the runtime to wait for the calling thread to return from this callback; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="0aa4c-109">I když hodnota `true` nebude mít vliv na modul runtime, může zkosit výsledky profilace.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-109">Although a value of `true` will not harm the runtime, it can skew the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0aa4c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0aa4c-110">Remarks</span></span>  
 <span data-ttu-id="0aa4c-111">Je možné získat více než jednu dvojici `JITCompilationStarted` a volání [ICorProfilerCallback:: JITCompilationFinished –](icorprofilercallback-jitcompilationfinished-method.md) pro jednotlivé funkce z důvodu způsobu, jakým modul runtime zpracovává konstruktory tříd.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-111">It is possible to receive more than one pair of `JITCompilationStarted` and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md) calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="0aa4c-112">Například modul runtime začíná metodou kompilace JIT A, ale je nutné spustit konstruktor třídy pro třídu B.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-112">For example, the runtime starts to JIT-compile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="0aa4c-113">Proto modul runtime JIT – zkompiluje konstruktor pro třídu B a spustí jej.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-113">Therefore, the runtime JIT-compiles the constructor for class B and runs it.</span></span> <span data-ttu-id="0aa4c-114">I když je konstruktor spuštěn, provede volání metody A, což způsobí, že metoda A bude znovu zkompilována kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-114">While the constructor is running, it makes a call to method A, which causes method A to be JIT-compiled again.</span></span> <span data-ttu-id="0aa4c-115">V tomto scénáři je první kompilace JIT metody A zastavena.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-115">In this scenario, the first JIT compilation of method A is halted.</span></span> <span data-ttu-id="0aa4c-116">Oba pokusy o metodu kompilace JIT A jsou však hlášeny s událostmi kompilace JIT.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-116">However, both attempts to JIT-compile method A are reported with JIT-compilation events.</span></span> <span data-ttu-id="0aa4c-117">Pokud profiler hodlá nahradit kód jazyka MSIL (Microsoft Intermediate Language) pro metodu A voláním metody [ICorProfilerInfo:: SetILFunctionBody –](icorprofilerinfo-setilfunctionbody-method.md) , musí to udělat pro obě `JITCompilationStarted` události, ale může použít stejný blok MSIL pro oba.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-117">If the profiler is going to replace Microsoft intermediate language (MSIL) code for method A by calling the [ICorProfilerInfo::SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method, it must do so for both `JITCompilationStarted` events, but it may use the same MSIL block for both.</span></span>  
  
 <span data-ttu-id="0aa4c-118">Profilery musí podporovat posloupnost zpětných volání JIT v případech, kdy dvě vlákna současně provádí zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-118">Profilers must support the sequence of JIT callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="0aa4c-119">Například vlákno A volání `JITCompilationStarted` .</span><span class="sxs-lookup"><span data-stu-id="0aa4c-119">For example, thread A calls `JITCompilationStarted`.</span></span> <span data-ttu-id="0aa4c-120">Nicméně před voláním vlákna `JITCompilationFinished` B vlákno B volá [ICorProfilerCallback:: EXCEPTIONSEARCHFUNCTIONENTER –](icorprofilercallback-exceptionsearchfunctionenter-method.md) s ID funkce z `JITCompilationStarted` zpětného volání vlákna A.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-120">However, before thread A calls `JITCompilationFinished`, thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from thread A's `JITCompilationStarted` callback.</span></span> <span data-ttu-id="0aa4c-121">Může se zdát, že ID funkce by ještě nemělo být platné, protože `JITCompilationFinished` Profiler zatím nepřijal volání.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-121">It might appear that the function ID should not yet be valid because a call to `JITCompilationFinished` had not yet been received by the profiler.</span></span> <span data-ttu-id="0aa4c-122">V takovém případě je však ID funkce platné.</span><span class="sxs-lookup"><span data-stu-id="0aa4c-122">However, in a case like this one, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa4c-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0aa4c-123">Requirements</span></span>  
 <span data-ttu-id="0aa4c-124">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa4c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa4c-125">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0aa4c-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0aa4c-126">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0aa4c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aa4c-127">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa4c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa4c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aa4c-128">See also</span></span>

- [<span data-ttu-id="0aa4c-129">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aa4c-129">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0aa4c-130">JITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="0aa4c-130">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
