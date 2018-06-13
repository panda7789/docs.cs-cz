---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted – metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ad74eeb4deeae73be40b3a0bc0f6a18ec2299780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454747"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a><span data-ttu-id="576ff-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted – metoda</span><span class="sxs-lookup"><span data-stu-id="576ff-102">ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method</span></span>
<span data-ttu-id="576ff-103">[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="576ff-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="576ff-104">Upozorní profileru vždy, když bylo zahájeno JIT – kompilace dynamické metody.</span><span class="sxs-lookup"><span data-stu-id="576ff-104">Notifies the profiler whenever JIT compilation of a dynamic method has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="576ff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="576ff-105">Syntax</span></span>  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="576ff-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="576ff-106">Parameters</span></span>  
<span data-ttu-id="576ff-107">[v] `functionId`</span><span class="sxs-lookup"><span data-stu-id="576ff-107">[in] `functionId`</span></span>  
<span data-ttu-id="576ff-108">Identifikátor funkce v paměti, pro které JIT kompilace spuštění.</span><span class="sxs-lookup"><span data-stu-id="576ff-108">The identifier of the in-memory function for which JIT compilation is started.</span></span>   

<span data-ttu-id="576ff-109">[v] `fIsSafeToBlock` </span><span class="sxs-lookup"><span data-stu-id="576ff-109">[in] `fIsSafeToBlock` </span></span>  
<span data-ttu-id="576ff-110">`true` k označení, že blokování může způsobit modulu runtime počkejte volající vlákno k návratu z této zpětného volání; `false` k označení, že blokování neovlivní operaci modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="576ff-110">`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

<span data-ttu-id="576ff-111">[v] `pILHeader`  </span><span class="sxs-lookup"><span data-stu-id="576ff-111">[in] `pILHeader`  </span></span>  
<span data-ttu-id="576ff-112">Ukazatel do prvního bajtu metoda IL hlavičky.</span><span class="sxs-lookup"><span data-stu-id="576ff-112">A pointer to the first byte of the method's IL header.</span></span>   

<span data-ttu-id="576ff-113">[v] `cbILHeader`  </span><span class="sxs-lookup"><span data-stu-id="576ff-113">[in] `cbILHeader`  </span></span>  
<span data-ttu-id="576ff-114">Počet bajtů v hlavičce IL.</span><span class="sxs-lookup"><span data-stu-id="576ff-114">The number of bytes in the IL header.</span></span> 

## <a name="remarks"></a><span data-ttu-id="576ff-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="576ff-115">Remarks</span></span>  

<span data-ttu-id="576ff-116">Vždy, když je dynamická metoda kompilována, aktivuje se tato zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="576ff-116">This callback is triggered whenever a dynamic method is JIT-compiled.</span></span> <span data-ttu-id="576ff-117">To zahrnuje různé IL zástupných procedur a LCG metody.</span><span class="sxs-lookup"><span data-stu-id="576ff-117">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="576ff-118">Jeho cílem je poskytnout dostatek informací k identifikaci kompilované metoda uživatelům profileru zapisovače.</span><span class="sxs-lookup"><span data-stu-id="576ff-118">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="576ff-119">`functionId` hodnoty nelze použít přeložit na jejich tokenů metadat, protože dynamické metody žádná metadata.</span><span class="sxs-lookup"><span data-stu-id="576ff-119">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

<span data-ttu-id="576ff-120">`pILHeader` Ukazatel je platná pouze během zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="576ff-120">The `pILHeader` pointer is only valid during the callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="576ff-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="576ff-121">Requirements</span></span>  
 <span data-ttu-id="576ff-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="576ff-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="576ff-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="576ff-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="576ff-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="576ff-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="576ff-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="576ff-125">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576ff-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="576ff-126">See Also</span></span>  
 [<span data-ttu-id="576ff-127">DynamicMethodJITCompilationFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="576ff-127">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)  
 [<span data-ttu-id="576ff-128">ICorProfilerCallback8 rozhraní</span><span class="sxs-lookup"><span data-stu-id="576ff-128">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
