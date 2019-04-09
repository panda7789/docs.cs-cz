---
title: ICorProfilerInfo3::EnumJITedFunctions – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7525d107fec7229d9b86eee63bde2aaf2d701b1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190298"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="826d6-102">ICorProfilerInfo3::EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="826d6-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="826d6-103">Vrátí enumerátor pro všechny funkce, které byly dříve zkompilován JIT Kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="826d6-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="826d6-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="826d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="826d6-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="826d6-106">[out] Ukazatel [icorprofilerfunctionenum –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerátor.</span><span class="sxs-lookup"><span data-stu-id="826d6-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="826d6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="826d6-107">Remarks</span></span>  
 <span data-ttu-id="826d6-108">Tato metoda se mohly překrývat s `JITCompilation` zpětná volání, jako [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="826d6-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="826d6-109">Enumerátor vrácený touto metodou neobsahuje funkce, které jsou načteny z nativní bitové kopie generované nástrojem Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="826d6-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="826d6-110">Vrácené výčet obsahuje pouze "0" pro hodnotu vlastnosti `COR_PRF_FUNCTION::reJitId` pole.</span><span class="sxs-lookup"><span data-stu-id="826d6-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="826d6-111">Pokud budete potřebovat platný `COR_PRF_FUNCTION::reJitId` hodnoty, použijte [icorprofilerinfo4::enumjitedfunctions2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="826d6-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826d6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="826d6-112">Requirements</span></span>  
 <span data-ttu-id="826d6-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="826d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826d6-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="826d6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="826d6-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="826d6-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="826d6-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="826d6-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="826d6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="826d6-117">See also</span></span>

- [<span data-ttu-id="826d6-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="826d6-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="826d6-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="826d6-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="826d6-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="826d6-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
