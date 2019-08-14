---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 79a1c80f1c7582bd0751c43dea1d35a4d4d1c661
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973741"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="7e4a7-102">ICorProfilerInfo10:: RequestReJITWithInliners – metoda</span><span class="sxs-lookup"><span data-stu-id="7e4a7-102">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>
  
<span data-ttu-id="7e4a7-103">ReJITs požadované metody, jakož i všechny zažádané metody.</span><span class="sxs-lookup"><span data-stu-id="7e4a7-103">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>   
  
## <a name="syntax"></a><span data-ttu-id="7e4a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e4a7-104">Syntax</span></span>  
  
```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```  
  
#### <a name="parameters"></a><span data-ttu-id="7e4a7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7e4a7-105">Parameters</span></span>  
 
 `dwRejitFlags` \
 <span data-ttu-id="7e4a7-106">pro Bitová maska [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7e4a7-106">[in] A bitmask of [COR_PRF_REJIT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-rejit-flags-enumeration.md).</span></span>
 
 `cFunctions`  
 <span data-ttu-id="7e4a7-107">pro Počet funkcí, které mají být rekompilovány.</span><span class="sxs-lookup"><span data-stu-id="7e4a7-107">[in] The number of functions to recompile.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="7e4a7-108">pro Určuje část párů (`module`, `methodDef`), které identifikují funkce, které mají být znovu zkompilovány. `moduleId`</span><span class="sxs-lookup"><span data-stu-id="7e4a7-108">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="7e4a7-109">pro Určuje část párů (`module`, `methodDef`), které identifikují funkce, které mají být znovu zkompilovány. `methodId`</span><span class="sxs-lookup"><span data-stu-id="7e4a7-109">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>  

## <a name="remarks"></a><span data-ttu-id="7e4a7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e4a7-110">Remarks</span></span>  
  <span data-ttu-id="7e4a7-111">[RequestReJIT –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) neprovádí žádné sledování s vloženými metodami.</span><span class="sxs-lookup"><span data-stu-id="7e4a7-111">[RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="7e4a7-112">Bylo očekáváno, že Profiler buď zablokuje vkládání, nebo sleduje vkládání `RequestReJIT` a volání všech zapsaných informací, aby bylo zajištěno, že všechny instance ReJITted metody byly vyvolány.</span><span class="sxs-lookup"><span data-stu-id="7e4a7-112">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="7e4a7-113">To představuje problém s ReJIT při připojení, protože Profiler není k dispozici pro monitorování vkládání.</span><span class="sxs-lookup"><span data-stu-id="7e4a7-113">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="7e4a7-114">Tuto metodu lze volat, aby bylo zaručeno, že celá sada linií ReJITted bude také.</span><span class="sxs-lookup"><span data-stu-id="7e4a7-114">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>  

## <a name="requirements"></a><span data-ttu-id="7e4a7-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e4a7-115">Requirements</span></span>  
 <span data-ttu-id="7e4a7-116">**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="7e4a7-116">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>  
  
 <span data-ttu-id="7e4a7-117">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e4a7-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e4a7-118">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e4a7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e4a7-119">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e4a7-119">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7e4a7-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e4a7-120">See also</span></span>
- [<span data-ttu-id="7e4a7-121">Rozhraní ICorProfilerInfo10</span><span class="sxs-lookup"><span data-stu-id="7e4a7-121">ICorProfilerInfo10 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)

