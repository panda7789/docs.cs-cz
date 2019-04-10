---
title: ICorProfilerFunctionControl – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 721ee27522b316a561e2f64a322c225cb85a44c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211436"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="2e1a5-102">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e1a5-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="2e1a5-103">Poskytuje metody, které umožňují profileru kód ke komunikaci s common language runtime (CLR) k řízení, jak by měl kompilátor JIT generování kódu při opětovné kompilaci konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="2e1a5-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e1a5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2e1a5-104">Methods</span></span>  
  
|<span data-ttu-id="2e1a5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2e1a5-105">Method</span></span>|<span data-ttu-id="2e1a5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2e1a5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e1a5-107">SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1a5-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="2e1a5-108">Nastaví jeden nebo více příznaků z [cor_prf_codegen_flags –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) překompilovány výčtu pro generování kódu pro ovládací prvek just-in-time (JIT) funkce.</span><span class="sxs-lookup"><span data-stu-id="2e1a5-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="2e1a5-109">SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1a5-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="2e1a5-110">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="2e1a5-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="2e1a5-111">SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1a5-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="2e1a5-112">Nastaví mapu kódu pro zadanou funkci pomocí zadané položky mapování Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="2e1a5-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e1a5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e1a5-113">Remarks</span></span>  
 <span data-ttu-id="2e1a5-114">`ICorProfilerFunctionControl` Rozhraní poskytuje metody pro řízení generování kódu pro jedinou překompilovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="2e1a5-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="2e1a5-115">Získá instanci tohoto rozhraní prostřednictvím profiler [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2e1a5-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="2e1a5-116">Každá instance `ICorProfilerFunctionControl` řídí všechny instance funkce.</span><span class="sxs-lookup"><span data-stu-id="2e1a5-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e1a5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e1a5-117">Requirements</span></span>  
 <span data-ttu-id="2e1a5-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e1a5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e1a5-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2e1a5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2e1a5-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e1a5-120">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2e1a5-121">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2e1a5-121">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2e1a5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e1a5-122">See also</span></span>

- [<span data-ttu-id="2e1a5-123">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e1a5-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="2e1a5-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2e1a5-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2e1a5-125">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="2e1a5-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
