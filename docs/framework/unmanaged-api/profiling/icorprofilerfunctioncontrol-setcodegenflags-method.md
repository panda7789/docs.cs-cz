---
title: ICorProfilerFunctionControl::SetCodegenFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 88c9f552b73af69ea4e1f64b75ed74ea762dcdfb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429936"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="4ce45-102">ICorProfilerFunctionControl::SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="4ce45-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="4ce45-103">Nastaví jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) pro řízení generování kódu pro rekompilován funkci just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="4ce45-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ce45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ce45-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ce45-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ce45-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="4ce45-106">pro Jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="4ce45-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ce45-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ce45-107">Remarks</span></span>  
 <span data-ttu-id="4ce45-108">Profiler získá instanci tohoto rozhraní prostřednictvím zpětného volání [ICorProfilerCallback4:: GetReJITParameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4ce45-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="4ce45-109">`SetCodegenFlags` umožňuje profileru řídit generování kódu pro rekompilovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="4ce45-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="4ce45-110">Stejně jako všechny ostatní parametry rekompilace JIT se příznaky generování kódu vztahují na všechny instance funkce.</span><span class="sxs-lookup"><span data-stu-id="4ce45-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="4ce45-111">Kompilátor JIT považuje tyto příznaky kompilace společně s dalšími příznaky určenými jinými zdroji při kompilování funkce.</span><span class="sxs-lookup"><span data-stu-id="4ce45-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="4ce45-112">Mezi ostatní zdroje patří ladicí program, globální příznaky nastavené profilerem při spuštění pomocí metody [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) (s hodnotami `COR_PRF_DISABLE_INLINING` a `COR_PRF_DISABLE_OPTIMIZATIONS`) a zpětným voláním [ICorProfilerCallback:: JITInlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="4ce45-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="4ce45-113">Kompilátor JIT dává přednost zdroji, který požaduje nejmenší množství optimalizace.</span><span class="sxs-lookup"><span data-stu-id="4ce45-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="4ce45-114">Například pokud profiler určí `COR_PRF_DISABLE_INLINING` při spuštění, ale neurčí `COR_PRF_CODEGEN_DISABLE_INLINING` ve zpětném volání [ICorProfilerFunctionControl:: SetCodegenFlags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) , vkládání je stále zakázáno.</span><span class="sxs-lookup"><span data-stu-id="4ce45-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="4ce45-115">Podobně platí, že pokud profiler neurčí `COR_PRF_CODEGEN_DISABLE_INLINING` v `SetCodegenFlags`, ale zakáže vkládání pomocí zpětného volání [ICorProfilerCallback:: JITInlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) , vkládání je zakázané.</span><span class="sxs-lookup"><span data-stu-id="4ce45-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ce45-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ce45-116">Requirements</span></span>  
 <span data-ttu-id="4ce45-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ce45-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ce45-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4ce45-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4ce45-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4ce45-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ce45-120">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ce45-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ce45-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ce45-121">See also</span></span>

- [<span data-ttu-id="4ce45-122">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ce45-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
