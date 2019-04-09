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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59104439"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="3dde9-102">ICorProfilerFunctionControl::SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="3dde9-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="3dde9-103">Nastaví jeden nebo více příznaků z [cor_prf_codegen_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) překompilovány výčtu pro generování kódu pro ovládací prvek just-in-time (JIT) funkce.</span><span class="sxs-lookup"><span data-stu-id="3dde9-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dde9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3dde9-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dde9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dde9-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="3dde9-106">[in] Jeden nebo více příznaků z [cor_prf_codegen_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="3dde9-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dde9-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3dde9-107">Remarks</span></span>  
 <span data-ttu-id="3dde9-108">Získá instanci tohoto rozhraní prostřednictvím profiler [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3dde9-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> `SetCodegenFlags` <span data-ttu-id="3dde9-109">Umožňuje profileru k řízení generování kódu pro rekompilované funkce.</span><span class="sxs-lookup"><span data-stu-id="3dde9-109">allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="3dde9-110">Stejně jako všechny ostatní JIT rekompilace parametry, příznaky generování kódu platí pro všechny instance funkce.</span><span class="sxs-lookup"><span data-stu-id="3dde9-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="3dde9-111">Kompilátor JIT bere v úvahu tyto příznaky kompilace, společně s další příznaky specifikovat z jiných zdrojů, při kompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="3dde9-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="3dde9-112">Další zdroje patří ladicí program, globální příznaky nastavením při spuštění pomocí profileru pomocí [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) – metoda (s hodnotami `COR_PRF_DISABLE_INLINING` a `COR_PRF_DISABLE_OPTIMIZATIONS`) a profileru [ Icorprofilercallback::jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3dde9-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="3dde9-113">Kompilátor JIT dává přednost před ke zdroji, který vyžaduje minimální množství optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3dde9-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="3dde9-114">Například, pokud profiler Určuje `COR_PRF_DISABLE_INLINING` při spuštění, ale neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) zpětné volání, vkládání je stále zakázáno.</span><span class="sxs-lookup"><span data-stu-id="3dde9-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="3dde9-115">Podobně pokud profiler neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v `SetCodegenFlags`, ale pak zakáže vkládání pomocí [icorprofilercallback::jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětné volání, vkládání je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="3dde9-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dde9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3dde9-116">Requirements</span></span>  
 <span data-ttu-id="3dde9-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dde9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dde9-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3dde9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3dde9-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dde9-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3dde9-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3dde9-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3dde9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3dde9-121">See also</span></span>

- [<span data-ttu-id="3dde9-122">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3dde9-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
