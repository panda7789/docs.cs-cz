---
title: ICorProfilerInfo3::GetFunctionEnter3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionEnter3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionEnter3Info
helpviewer_keywords:
- GetFunctionEnter3Info method [.NET Framework profiling]
- ICorProfilerInfo3::GetFunctionEnter3Info method [.NET Framework profiling]
ms.assetid: 542c7c65-dd56-4651-b76f-5db2465e4a15
topic_type:
- apiref
ms.openlocfilehash: 876ae07a432bfa36a7d9f43ae6c32ec03d7d3289
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496591"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="79c9d-102">ICorProfilerInfo3::GetFunctionEnter3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="79c9d-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="79c9d-103">Poskytuje informace o snímku zásobníku a argumentu funkce, která je hlášena v profileru funkcí [FunctionEnter3WithInfo –](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="79c9d-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="79c9d-104">Tuto metodu lze volat pouze během `FunctionEnter3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="79c9d-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79c9d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79c9d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79c9d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="79c9d-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="79c9d-107">pro `FunctionID`Funkce, která se zadává.</span><span class="sxs-lookup"><span data-stu-id="79c9d-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="79c9d-108">pro Neprůhledný popisovač, který představuje informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="79c9d-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="79c9d-109">Profiler by měl poskytnout stejný, jako by `eltInfo` byl dán funkcí [FunctionEnter3WithInfo –](functionenter3withinfo-function.md) .</span><span class="sxs-lookup"><span data-stu-id="79c9d-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="79c9d-110">mimo Neprůhledný popisovač, který představuje obecné informace o daném snímku zásobníku.</span><span class="sxs-lookup"><span data-stu-id="79c9d-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="79c9d-111">Tento popisovač je platný pouze během `FunctionEnter3WithInfo` zpětného volání, ve kterém Profiler volal `GetFunctionEnter3Info` metodu.</span><span class="sxs-lookup"><span data-stu-id="79c9d-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="79c9d-112">[in, out] Ukazatel na celkovou velikost [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury (včetně všech dalších [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktur pro rozsahy argumentů, na které ukazuje `pArgumentInfo` ).</span><span class="sxs-lookup"><span data-stu-id="79c9d-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="79c9d-113">Pokud zadaná velikost není dostatečná, je vrácena ERROR_INSUFFICIENT_BUFFER a očekávaná velikost je uložena v `pcbArgumentInfo` .</span><span class="sxs-lookup"><span data-stu-id="79c9d-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="79c9d-114">Chcete-li volat `GetFunctionEnter3Info` pouze pro načtení očekávané hodnoty pro `*pcbArgumentInfo` , nastavte `*pcbArgumentInfo` = 0 a `pArgumentInfo` = null.</span><span class="sxs-lookup"><span data-stu-id="79c9d-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="79c9d-115">mimo Ukazatel na [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) strukturu, která popisuje umístění argumentů funkce v paměti v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="79c9d-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79c9d-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79c9d-116">Remarks</span></span>  
 <span data-ttu-id="79c9d-117">Profiler musí přidělit dostatek místa pro `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu kontrolované funkce a musí indikovat velikost v `pcbArgumentInfo` parametru.</span><span class="sxs-lookup"><span data-stu-id="79c9d-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79c9d-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="79c9d-118">Requirements</span></span>  
 <span data-ttu-id="79c9d-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79c9d-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79c9d-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="79c9d-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="79c9d-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="79c9d-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79c9d-122">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79c9d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79c9d-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79c9d-123">See also</span></span>

- [<span data-ttu-id="79c9d-124">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="79c9d-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="79c9d-125">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="79c9d-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="79c9d-126">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="79c9d-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="79c9d-127">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="79c9d-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="79c9d-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="79c9d-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="79c9d-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="79c9d-129">Profiling</span></span>](index.md)
