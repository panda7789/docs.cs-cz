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
ms.openlocfilehash: add89fe81fccbd5e6f5ad5d27f0ab3ace489963e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868522"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="11788-102">ICorProfilerInfo3::GetFunctionTailcall3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="11788-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="11788-103">Poskytuje rámec zásobníku funkce, která je hlášena profileru funkcí [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="11788-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="11788-104">Tuto metodu lze volat pouze během `FunctionTailcall3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="11788-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11788-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11788-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11788-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="11788-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="11788-107">pro `FunctionID` funkce, která vrací.</span><span class="sxs-lookup"><span data-stu-id="11788-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="11788-108">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="11788-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="11788-109">Profiler by měl poskytnout stejnou `eltInfo`, která byla přidělena profileru funkcí `FunctionTailcall3WithInfo`.</span><span class="sxs-lookup"><span data-stu-id="11788-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="11788-110">mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="11788-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="11788-111">Tento popisovač je platný pouze během `FunctionTailcall3WithInfo` zpětného volání, ve kterém Profiler volal metodu `GetFunctionTailcall3Info`.</span><span class="sxs-lookup"><span data-stu-id="11788-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11788-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11788-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11788-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="11788-113">Requirements</span></span>  
 <span data-ttu-id="11788-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11788-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11788-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="11788-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="11788-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11788-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11788-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11788-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11788-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11788-118">See also</span></span>

- [<span data-ttu-id="11788-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="11788-119">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="11788-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="11788-120">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="11788-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="11788-121">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="11788-122">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="11788-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="11788-123">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="11788-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="11788-124">Profilace</span><span class="sxs-lookup"><span data-stu-id="11788-124">Profiling</span></span>](index.md)
