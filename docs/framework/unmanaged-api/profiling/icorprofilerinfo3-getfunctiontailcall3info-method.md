---
title: ICorProfilerInfo3::GetFunctionTailcall3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: 5346792cb2a1309268cb4ba48625aa559777fbaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176991"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="1cf63-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="1cf63-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="1cf63-103">Poskytuje rámec zásobníku funkce, která je hlášena profiler funkcí [FunctionTailcall3WithInfo.](functiontailcall3withinfo-function.md)</span><span class="sxs-lookup"><span data-stu-id="1cf63-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="1cf63-104">Tuto metodu lze volat `FunctionTailcall3WithInfo` pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="1cf63-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cf63-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cf63-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cf63-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1cf63-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="1cf63-107">[v] Funkce, `FunctionID` která se vrací.</span><span class="sxs-lookup"><span data-stu-id="1cf63-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="1cf63-108">[v] Neprůhledný popisovač, který představuje informace o daném rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1cf63-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="1cf63-109">Profiler by měl `eltInfo` poskytnout stejné, které bylo `FunctionTailcall3WithInfo` dáno profiler funkce.</span><span class="sxs-lookup"><span data-stu-id="1cf63-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="1cf63-110">[out] Neprůhledný popisovač, který představuje obecné informace o daném rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1cf63-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="1cf63-111">Tento popisovač je `FunctionTailcall3WithInfo` platný pouze během zpětného `GetFunctionTailcall3Info` volání, ve kterém profiler volal metodu.</span><span class="sxs-lookup"><span data-stu-id="1cf63-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cf63-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1cf63-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cf63-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1cf63-113">Requirements</span></span>  
 <span data-ttu-id="1cf63-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cf63-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cf63-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1cf63-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1cf63-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cf63-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cf63-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cf63-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cf63-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1cf63-118">See also</span></span>

- [<span data-ttu-id="1cf63-119">FunkceEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="1cf63-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="1cf63-120">FunkceLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="1cf63-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="1cf63-121">FunkceTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="1cf63-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="1cf63-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1cf63-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1cf63-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1cf63-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1cf63-124">Profilování</span><span class="sxs-lookup"><span data-stu-id="1cf63-124">Profiling</span></span>](index.md)
