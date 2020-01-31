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
ms.openlocfilehash: 1286ce953c96eb3e3164ba5b209031dd1ec5c453
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864697"
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="494cb-102">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="494cb-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="494cb-103">Poskytuje metody, které umožňují, aby Profiler kódu komunikoval s modulem CLR (Common Language Runtime), který řídí, jak by kompilátor JIT měl generovat kód při rekompilaci konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="494cb-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="494cb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="494cb-104">Methods</span></span>  
  
|<span data-ttu-id="494cb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="494cb-105">Method</span></span>|<span data-ttu-id="494cb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="494cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="494cb-107">SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="494cb-107">SetCodegenFlags Method</span></span>](icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="494cb-108">Nastaví jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) pro řízení generování kódu pro rekompilován funkci just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="494cb-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="494cb-109">SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="494cb-109">SetILFunctionBody Method</span></span>](icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="494cb-110">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="494cb-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="494cb-111">SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="494cb-111">SetILInstrumentedCodeMap Method</span></span>](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="494cb-112">Nastaví mapu kódu pro určenou funkci pomocí zadaných položek mapování Common Intermediate Language (CIL).</span><span class="sxs-lookup"><span data-stu-id="494cb-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="494cb-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="494cb-113">Remarks</span></span>  
 <span data-ttu-id="494cb-114">Rozhraní `ICorProfilerFunctionControl` poskytuje metody pro řízení generování kódu pro jednu rekompilovaný funkce.</span><span class="sxs-lookup"><span data-stu-id="494cb-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="494cb-115">Profiler získá instanci tohoto rozhraní prostřednictvím zpětného volání [ICorProfilerCallback4:: GetReJITParameters –](icorprofilercallback4-getrejitparameters-method.md) .</span><span class="sxs-lookup"><span data-stu-id="494cb-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="494cb-116">Každá instance `ICorProfilerFunctionControl` řídí všechny instance jedné funkce.</span><span class="sxs-lookup"><span data-stu-id="494cb-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="494cb-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="494cb-117">Requirements</span></span>  
 <span data-ttu-id="494cb-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="494cb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="494cb-119">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="494cb-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="494cb-120">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="494cb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="494cb-121">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="494cb-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="494cb-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="494cb-122">See also</span></span>

- [<span data-ttu-id="494cb-123">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="494cb-123">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="494cb-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="494cb-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="494cb-125">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="494cb-125">EnumJITedFunctions2 Method</span></span>](icorprofilerinfo4-enumjitedfunctions2-method.md)
