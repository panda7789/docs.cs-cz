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
ms.openlocfilehash: 43c32d1ce4f804da8980dc0c566a77e5b076661b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459610"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a><span data-ttu-id="2df58-102">ICorProfilerFunctionControl::SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2df58-102">ICorProfilerFunctionControl::SetCodegenFlags Method</span></span>
<span data-ttu-id="2df58-103">Nastaví jeden nebo více příznaků z [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) výčtu pro generování kódu ovládacího prvku pro v běhu (JIT) překompilovat funkce.</span><span class="sxs-lookup"><span data-stu-id="2df58-103">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2df58-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2df58-104">Syntax</span></span>  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2df58-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2df58-105">Parameters</span></span>  
 `flags`  
 <span data-ttu-id="2df58-106">[v] Jeden nebo více příznaků z [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="2df58-106">[in] One or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2df58-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2df58-107">Remarks</span></span>  
 <span data-ttu-id="2df58-108">Získá instanci tohoto rozhraní prostřednictvím profileru [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2df58-108">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="2df58-109">`SetCodegenFlags` umožňuje řídit generování kódu pro funkci Rekompilované profileru.</span><span class="sxs-lookup"><span data-stu-id="2df58-109">`SetCodegenFlags` allows the profiler to control the code generation for the recompiled function.</span></span> <span data-ttu-id="2df58-110">Stejně jako u všech dalších JIT rekompilace parametrů, příznaky generování kódu platí pro všechny instance funkce.</span><span class="sxs-lookup"><span data-stu-id="2df58-110">As with all other JIT recompilation parameters, the code generation flags apply to all instances of the function.</span></span>  
  
 <span data-ttu-id="2df58-111">Kompilátor JIT zvažuje tyto příznaky kompilace, společně s další příznaky určeného jiných zdrojů, když kompilujete funkce.</span><span class="sxs-lookup"><span data-stu-id="2df58-111">The JIT compiler considers these compilation flags, along with other flags specified by other sources, when compiling a function.</span></span>  <span data-ttu-id="2df58-112">U jiných zdrojů zahrnují ladicího programu, globální příznaky nastavit profileru při spuštění pomocí pomocí [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) – metoda (s hodnotami `COR_PRF_DISABLE_INLINING` a `COR_PRF_DISABLE_OPTIMIZATIONS`) a profileru [ Icorprofilercallback::jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2df58-112">The other sources include the debugger, global flags set by the profiler on startup by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method (with the values `COR_PRF_DISABLE_INLINING` and `COR_PRF_DISABLE_OPTIMIZATIONS`), and the profiler’s [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback.</span></span>  <span data-ttu-id="2df58-113">Kompilátor JIT dává přednost ke zdroji, které vyžadují nejnižší možné optimalizace.</span><span class="sxs-lookup"><span data-stu-id="2df58-113">The JIT compiler gives precedence to a source that requests the least amount of optimizing.</span></span>  <span data-ttu-id="2df58-114">Například, pokud profileru Určuje `COR_PRF_DISABLE_INLINING` při spuštění, ale neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v [icorprofilerfunctioncontrol::setcodegenflags –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) zpětné volání, vložené stále vypnutá.</span><span class="sxs-lookup"><span data-stu-id="2df58-114">For example, if the profiler specifies `COR_PRF_DISABLE_INLINING` on startup, but does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in the [ICorProfilerFunctionControl::SetCodegenFlags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) callback, inlining is still disabled.</span></span>  <span data-ttu-id="2df58-115">Podobně pokud profileru neurčuje `COR_PRF_CODEGEN_DISABLE_INLINING` v `SetCodegenFlags`, ale pak zakáže vložené pomocí [icorprofilercallback::jitinlining –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) zpětné volání, vložené je zakázána.</span><span class="sxs-lookup"><span data-stu-id="2df58-115">Similarly, if the profiler does not specify `COR_PRF_CODEGEN_DISABLE_INLINING` in `SetCodegenFlags`, but then disables inlining by using the [ICorProfilerCallback::JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callback, inlining is disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df58-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2df58-116">Requirements</span></span>  
 <span data-ttu-id="2df58-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df58-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df58-118">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2df58-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2df58-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df58-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df58-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df58-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df58-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2df58-121">See Also</span></span>  
 [<span data-ttu-id="2df58-122">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df58-122">ICorProfilerFunctionControl Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
