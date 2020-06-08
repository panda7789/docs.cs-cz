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
ms.openlocfilehash: e4d0d9ed07c707e51e5833483b71079f2c330505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496526"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="cb07c-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="cb07c-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="cb07c-103">Poskytuje rámec zásobníku funkce, která je hlášena profileru funkcí [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="cb07c-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="cb07c-104">Tuto metodu lze volat pouze během `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="cb07c-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb07c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb07c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb07c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb07c-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cb07c-107">pro `FunctionID`Funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="cb07c-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="cb07c-108">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cb07c-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="cb07c-109">Profiler by měl poskytnout stejnou `eltInfo` funkci, která byla přidělena profileru `FunctionTailcall3WithInfo` funkcí.</span><span class="sxs-lookup"><span data-stu-id="cb07c-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="cb07c-110">mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="cb07c-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="cb07c-111">Tento popisovač je platný pouze během `FunctionTailcall3WithInfo` zpětného volání, ve kterém Profiler volal `GetFunctionTailcall3Info` metodu.</span><span class="sxs-lookup"><span data-stu-id="cb07c-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb07c-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cb07c-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb07c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb07c-113">Requirements</span></span>  
 <span data-ttu-id="cb07c-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb07c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb07c-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cb07c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cb07c-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cb07c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb07c-117">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb07c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb07c-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb07c-118">See also</span></span>

- [<span data-ttu-id="cb07c-119">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="cb07c-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="cb07c-120">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="cb07c-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="cb07c-121">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="cb07c-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="cb07c-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb07c-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cb07c-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="cb07c-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cb07c-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="cb07c-124">Profiling</span></span>](index.md)
