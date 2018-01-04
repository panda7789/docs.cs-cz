---
title: "ICorProfilerFunctionControl – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionControl
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionControl
helpviewer_keywords: ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 043e97595ba29d0fb5320b8f1bdc4aad4f755067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctioncontrol-interface"></a><span data-ttu-id="544e5-102">ICorProfilerFunctionControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="544e5-102">ICorProfilerFunctionControl Interface</span></span>
<span data-ttu-id="544e5-103">Poskytuje metody, které umožňují kódu profileru ke komunikaci s modul CLR (CLR) k řízení, jak by měla JIT kompilátoru generování kódu při nutnosti rekompilace konkrétní metody.</span><span class="sxs-lookup"><span data-stu-id="544e5-103">Provides methods that allow a code profiler to communicate with the common language runtime (CLR) to control how the JIT compiler should generate code when recompiling a specific method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="544e5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="544e5-104">Methods</span></span>  
  
|<span data-ttu-id="544e5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="544e5-105">Method</span></span>|<span data-ttu-id="544e5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="544e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="544e5-107">SetCodegenFlags – metoda</span><span class="sxs-lookup"><span data-stu-id="544e5-107">SetCodegenFlags Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|<span data-ttu-id="544e5-108">Nastaví jeden nebo více příznaků z [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) výčtu pro generování kódu ovládacího prvku pro v běhu (JIT) překompilovat funkce.</span><span class="sxs-lookup"><span data-stu-id="544e5-108">Sets one or more flags from the [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) enumeration to control code generation for a just-in-time (JIT) recompiled function.</span></span>|  
|[<span data-ttu-id="544e5-109">SetILFunctionBody – metoda</span><span class="sxs-lookup"><span data-stu-id="544e5-109">SetILFunctionBody Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|<span data-ttu-id="544e5-110">Nahrazuje tělo Common Intermediate Language (CIL) metody.</span><span class="sxs-lookup"><span data-stu-id="544e5-110">Replaces the Common Intermediate Language (CIL) body of the method.</span></span>|  
|[<span data-ttu-id="544e5-111">SetILInstrumentedCodeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="544e5-111">SetILInstrumentedCodeMap Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|<span data-ttu-id="544e5-112">Nastaví mapu kódu pro zadanou funkci pomocí zadané položek mapování Common mezilehlá jazyk (CIL).</span><span class="sxs-lookup"><span data-stu-id="544e5-112">Sets a code map for the specified function by using the specified Common Intermediate Language (CIL) map entries.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="544e5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="544e5-113">Remarks</span></span>  
 <span data-ttu-id="544e5-114">`ICorProfilerFunctionControl` Rozhraní poskytuje metody pro generování kódu pro jedné Rekompilované funkce řízení.</span><span class="sxs-lookup"><span data-stu-id="544e5-114">The `ICorProfilerFunctionControl` interface provides methods for controlling code generation for a single recompiled function.</span></span> <span data-ttu-id="544e5-115">Získá instanci tohoto rozhraní prostřednictvím profileru [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="544e5-115">The profiler obtains an instance of this interface through the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) callback.</span></span> <span data-ttu-id="544e5-116">Každá instance `ICorProfilerFunctionControl` všechny instance jednu funkci ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="544e5-116">Each instance of `ICorProfilerFunctionControl` controls all instances of one function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="544e5-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="544e5-117">Requirements</span></span>  
 <span data-ttu-id="544e5-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="544e5-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="544e5-119">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="544e5-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="544e5-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="544e5-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="544e5-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="544e5-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="544e5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="544e5-122">See Also</span></span>  
 [<span data-ttu-id="544e5-123">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="544e5-123">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="544e5-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="544e5-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="544e5-125">EnumJITedFunctions2 – metoda</span><span class="sxs-lookup"><span data-stu-id="544e5-125">EnumJITedFunctions2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
