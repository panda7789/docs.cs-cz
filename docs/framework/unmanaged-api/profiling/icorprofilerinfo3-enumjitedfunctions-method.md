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
ms.openlocfilehash: a22a0de9a20f32ce1c9818bbcf29222a4b331420
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862422"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="27e2a-102">ICorProfilerInfo3::EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="27e2a-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="27e2a-103">Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT.</span><span class="sxs-lookup"><span data-stu-id="27e2a-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27e2a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27e2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27e2a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="27e2a-106">mimo Ukazatel na enumerátor [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="27e2a-106">[out] A pointer to the [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27e2a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="27e2a-107">Remarks</span></span>  
 <span data-ttu-id="27e2a-108">Tato metoda se může překrývat s `JITCompilation`mi zpětnými voláními, jako je například metoda [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27e2a-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="27e2a-109">Enumerátor vrácený touto metodou nezahrnuje funkce, které jsou načteny z nativních imagí vygenerovaných pomocí nástroje Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="27e2a-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27e2a-110">Vrácený výčet obsahuje pouze "0" pro hodnotu pole `COR_PRF_FUNCTION::reJitId`.</span><span class="sxs-lookup"><span data-stu-id="27e2a-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="27e2a-111">Pokud požadujete platné `COR_PRF_FUNCTION::reJitId` hodnoty, použijte metodu [ICorProfilerInfo4:: EnumJITedFunctions2 –](icorprofilerinfo4-enumjitedfunctions2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="27e2a-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27e2a-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27e2a-112">Requirements</span></span>  
 <span data-ttu-id="27e2a-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27e2a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27e2a-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="27e2a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27e2a-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="27e2a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27e2a-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27e2a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e2a-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27e2a-117">See also</span></span>

- [<span data-ttu-id="27e2a-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="27e2a-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="27e2a-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="27e2a-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="27e2a-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="27e2a-120">Profiling</span></span>](index.md)
