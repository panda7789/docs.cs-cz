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
ms.openlocfilehash: a3d5527fc34ad7292974c005179e9d9cad210c94
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503117"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="e7a1b-102">ICorProfilerFunctionControl::SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="e7a1b-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="e7a1b-103">Nastaví jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) pro řízení generování kódu pro rekompilován funkci just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="e7a1b-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7a1b-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7a1b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e7a1b-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="e7a1b-106">pro Jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="e7a1b-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7a1b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7a1b-107">Remarks</span></span>  
 <span data-ttu-id="e7a1b-108">Profiler získá instanci tohoto rozhraní prostřednictvím zpětného volání [ICorProfilerCallback4:: GetReJITParameters –](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e7a1b-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="e7a1b-109">`SetCodegenFlags`umožňuje profileru řídit generování kódu pro rekompilovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="e7a1b-110">Stejně jako všechny ostatní parametry rekompilace JIT se příznaky generování kódu vztahují na všechny instance funkce.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="e7a1b-111">Kompilátor JIT považuje tyto příznaky kompilace společně s dalšími příznaky určenými jinými zdroji při kompilování funkce.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="e7a1b-112">Mezi ostatní zdroje patří ladicí program, globální příznaky nastavené profilerem při spuštění pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) (s hodnotami `COR_PRF_DISABLE_INLINING` a `COR_PRF_DISABLE_OPTIMIZATIONS` ) a zpětným voláním [ICorProfilerCallback:: JITInlining –](icorprofilercallback-jitinlining-method.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="e7a1b-113">Kompilátor JIT dává přednost zdroji, který požaduje nejmenší množství optimalizace.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="e7a1b-114">Například pokud profiler určí `COR_PRF_DISABLE_INLINING` při spuštění, ale neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` ve zpětném volání [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) , vkládání je stále zakázáno.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="e7a1b-115">Podobně platí, že pokud profiler neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v `SetCodegenFlags` , ale zakáže vkládání pomocí zpětného volání [ICorProfilerCallback:: JITInlining –](icorprofilercallback-jitinlining-method.md) , je vkládání vypnuto.</span><span class="sxs-lookup"><span data-stu-id="e7a1b-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a1b-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7a1b-116">Requirements</span></span>  
 <span data-ttu-id="e7a1b-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a1b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a1b-118">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e7a1b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7a1b-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e7a1b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7a1b-120">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a1b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a1b-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7a1b-121">See also</span></span>

- [<span data-ttu-id="e7a1b-122">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7a1b-122">ICorProfilerFunctionControl Interface</span></span>](icorprofilerfunctioncontrol-interface.md)
