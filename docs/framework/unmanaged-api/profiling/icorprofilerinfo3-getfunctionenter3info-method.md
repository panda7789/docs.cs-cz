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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5d06988330b9ec83463165661ea5425d8563c60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459052"
---
# <a name="icorprofilerinfo3getfunctionenter3info-method"></a><span data-ttu-id="47a8b-102">ICorProfilerInfo3::GetFunctionEnter3Info – metoda</span><span class="sxs-lookup"><span data-stu-id="47a8b-102">ICorProfilerInfo3::GetFunctionEnter3Info Method</span></span>
<span data-ttu-id="47a8b-103">Poskytuje informace zásobníku rámec a argument funkce, která je hlášena profileru pomocí [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="47a8b-103">Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span> <span data-ttu-id="47a8b-104">Tuto metodu lze volat pouze během `FunctionEnter3WithInfo` zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="47a8b-104">This method can be called only during the `FunctionEnter3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a8b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47a8b-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionEnter3Info(  
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo,  
            [in, out] ULONG *pcbArgumentInfo,  
            [out, size_is(*pcbArgumentInfo)]  
                  COR_PRF_FUNCTION_ARGUMENT_INFO *pArgumentInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47a8b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="47a8b-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="47a8b-107">[v] `FunctionID` Funkce, který jste právě zadali.</span><span class="sxs-lookup"><span data-stu-id="47a8b-107">[in] The `FunctionID` of the function that is being entered.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="47a8b-108">[v] Neprůhledného popisovače, který představuje informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="47a8b-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="47a8b-109">Profileru by měl poskytovat stejné `eltInfo` se určí podle [functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="47a8b-109">The profiler should provide the same `eltInfo` that it was given by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="47a8b-110">[out] Neprůhledného popisovače, který představuje obecné informace o daném zásobníku.</span><span class="sxs-lookup"><span data-stu-id="47a8b-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="47a8b-111">Tento popisovač je platný pouze během `FunctionEnter3WithInfo` zpětného volání, ve kterém se nazývá profileru `GetFunctionEnter3Info` metoda.</span><span class="sxs-lookup"><span data-stu-id="47a8b-111">This handle is valid only during the `FunctionEnter3WithInfo` callback in which the profiler called the `GetFunctionEnter3Info` method.</span></span>  
  
 `pcbArgumentInfo`  
 <span data-ttu-id="47a8b-112">[ve out] Ukazatel na celkovou velikost v bajtech z [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) strukturu (a všechny další [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktury pro argument rozsahy, na kterou odkazuje`pArgumentInfo`).</span><span class="sxs-lookup"><span data-stu-id="47a8b-112">[in, out] A pointer to the total size, in bytes, of the [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure (plus any additional [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structures for the argument ranges pointed to by `pArgumentInfo`).</span></span> <span data-ttu-id="47a8b-113">Pokud po zadanou velikost není dost, je vrácen ERROR_INSUFFICIENT_BUFFER a očekávané velikosti je uložen v `pcbArgumentInfo`.</span><span class="sxs-lookup"><span data-stu-id="47a8b-113">If the specified size is not enough, ERROR_INSUFFICIENT_BUFFER is returned and the expected size is stored in `pcbArgumentInfo`.</span></span> <span data-ttu-id="47a8b-114">K volání `GetFunctionEnter3Info` jenom k načtení očekávaná hodnota pro `*pcbArgumentInfo`, nastavte `*pcbArgumentInfo`= 0 a `pArgumentInfo`= NULL.</span><span class="sxs-lookup"><span data-stu-id="47a8b-114">To call `GetFunctionEnter3Info` just to retrieve the expected value for `*pcbArgumentInfo`, set `*pcbArgumentInfo`=0 and `pArgumentInfo`=NULL.</span></span>  
  
 `pArgumentInfo`  
 <span data-ttu-id="47a8b-115">[out] Ukazatel [cor_prf_function_argument_info –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) struktura, která popisuje umístění argumenty v paměti, v pořadí zleva doprava.</span><span class="sxs-lookup"><span data-stu-id="47a8b-115">[out] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that describes the locations of the function's arguments in memory, in left-to-right order.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47a8b-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47a8b-116">Remarks</span></span>  
 <span data-ttu-id="47a8b-117">Profileru přidělíte dostatek místa pro `COR_PRF_FUNCTION_ARGUMENT_INFO` Struktura funkce, která je ke kontrole a musí označovat velikost v `pcbArgumentInfo` parametr.</span><span class="sxs-lookup"><span data-stu-id="47a8b-117">The profiler must allocate sufficient space for the `COR_PRF_FUNCTION_ARGUMENT_INFO` structure of the function that is being inspected, and must indicate the size in the `pcbArgumentInfo` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a8b-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47a8b-118">Requirements</span></span>  
 <span data-ttu-id="47a8b-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a8b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a8b-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="47a8b-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47a8b-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47a8b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47a8b-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a8b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a8b-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="47a8b-123">See Also</span></span>  
 [<span data-ttu-id="47a8b-124">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="47a8b-124">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="47a8b-125">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="47a8b-125">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="47a8b-126">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="47a8b-126">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="47a8b-127">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="47a8b-127">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="47a8b-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="47a8b-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="47a8b-129">Profilace</span><span class="sxs-lookup"><span data-stu-id="47a8b-129">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
