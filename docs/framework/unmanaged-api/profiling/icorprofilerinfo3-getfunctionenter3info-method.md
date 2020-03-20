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
ms.openlocfilehash: 50d16b8036144d6ede349149fa4ae37344064d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177017"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="74f91-102">ICorProfilerInfo3::GetFunctionEnter3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="74f91-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="74f91-103">Poskytuje zásobníku rámce a argument informace o funkci, která je hlášena profiler funkce [FunctionEnter3WithInfo](functionenter3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="74f91-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="74f91-104">Tuto metodu lze volat `FunctionEnter3WithInfo` pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="74f91-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f91-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74f91-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74f91-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="74f91-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="74f91-107">[v] Funkce, `FunctionID` která je zadána.</span><span class="sxs-lookup"><span data-stu-id="74f91-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="74f91-108">[v] Neprůhledný popisovač, který představuje informace o daném rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="74f91-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="74f91-109">Profiler by měl `eltInfo` poskytnout stejné, které bylo dáno [functionEnter3WithInfo](functionenter3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="74f91-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="74f91-110">[out] Neprůhledný popisovač, který představuje obecné informace o daném rámci zásobníku.</span><span class="sxs-lookup"><span data-stu-id="74f91-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="74f91-111">Tento popisovač je `FunctionEnter3WithInfo` platný pouze během zpětného `GetFunctionEnter3Info` volání, ve kterém profiler volal metodu.</span><span class="sxs-lookup"><span data-stu-id="74f91-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="74f91-112">[dovnitř, ven] Ukazatel na celkovou velikost [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury v bajtech (plus všechny další [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktury pro `pArgumentInfo`rozsahy argumentů, na které odkazuje ).</span><span class="sxs-lookup"><span data-stu-id="74f91-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="74f91-113">Pokud zadaná velikost nestačí, ERROR_INSUFFICIENT_BUFFER je vrácena `pcbArgumentInfo`a očekávaná velikost je uložena v .</span><span class="sxs-lookup"><span data-stu-id="74f91-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="74f91-114">Chcete-li `GetFunctionEnter3Info` volat pouze pro `*pcbArgumentInfo`načtení očekávané hodnoty pro , nastavte `*pcbArgumentInfo`=0 a `pArgumentInfo`=NULL.</span><span class="sxs-lookup"><span data-stu-id="74f91-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="74f91-115">[out] Ukazatel na [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) struktury, která popisuje umístění argumentů funkce v paměti, v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="74f91-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74f91-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74f91-116">Remarks</span></span>  
 <span data-ttu-id="74f91-117">Profiler musí přidělit dostatek `COR_PRF_FUNCTION_ARGUMENT_INFO` místa pro strukturu funkce, která je kontrolována `pcbArgumentInfo` a musí uvádět velikost v parametru.</span><span class="sxs-lookup"><span data-stu-id="74f91-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74f91-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74f91-118">Requirements</span></span>  
 <span data-ttu-id="74f91-119">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74f91-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f91-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74f91-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74f91-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74f91-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74f91-122">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f91-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f91-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="74f91-123">See also</span></span>

- [<span data-ttu-id="74f91-124">FunkceEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="74f91-124">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="74f91-125">FunkceLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="74f91-125">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="74f91-126">FunkceTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="74f91-126">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="74f91-127">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74f91-127">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="74f91-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="74f91-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="74f91-129">Profilování</span><span class="sxs-lookup"><span data-stu-id="74f91-129">Profiling</span></span>](index.md)
