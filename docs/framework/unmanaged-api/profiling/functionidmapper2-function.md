---
title: FunctionIDMapper2 – funkce
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a236dcae29d00afe3b72dce8f81d657fb4fac28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598919"
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="c7462-102">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="c7462-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="c7462-103">Oznámí profileru, že daný identifikátor funkce může přemapován na alternativní ID se použije v [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) zpětná volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="c7462-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="c7462-104">`FunctionIDMapper2` také umožňuje profileru označíte, zda si přeje přijmout zpětná volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="c7462-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7462-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7462-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7462-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c7462-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="c7462-107">[in] Identifikátor funkce pro přemapování.</span><span class="sxs-lookup"><span data-stu-id="c7462-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="c7462-108">[in] Ukazatel na data, která se používá k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="c7462-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="c7462-109">[out] Ukazatel na hodnotu, která profiler nastaví na `true` Pokud chce přijmout `FunctionEnter3`, `FunctionLeave3`, a `FunctionTailcall3`, nebo `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, a `FunctionTailcall3WithInfo` zpětná volání; jinak nastaví tuto hodnotu a `false`.</span><span class="sxs-lookup"><span data-stu-id="c7462-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7462-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c7462-110">Return Value</span></span>  
 <span data-ttu-id="c7462-111">Profiler vrací hodnotu, která spouštěcí modul používá jako alternativní identifikátor funkce.</span><span class="sxs-lookup"><span data-stu-id="c7462-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="c7462-112">Návratová hodnota nemůže mít hodnotu null není-li `false` se vrátí v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="c7462-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="c7462-113">Jinak nulová návratová hodnota vytváří nepředvídatelné výsledky včetně případného zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="c7462-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7462-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7462-114">Remarks</span></span>  
 <span data-ttu-id="c7462-115">Tato metoda rozšiřuje [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce s dalším parametrem, který se používá k předávání dat klienta.</span><span class="sxs-lookup"><span data-stu-id="c7462-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="c7462-116">Data klienta se používají k rozlišování mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="c7462-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7462-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7462-117">Requirements</span></span>  
 <span data-ttu-id="c7462-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7462-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7462-119">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="c7462-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c7462-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7462-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7462-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7462-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7462-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7462-122">See also</span></span>

- [<span data-ttu-id="c7462-123">ICorProfilerInfo::SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="c7462-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="c7462-124">ICorProfilerInfo3::SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="c7462-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="c7462-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c7462-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="c7462-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="c7462-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="c7462-127">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="c7462-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="c7462-128">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c7462-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="c7462-129">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c7462-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="c7462-130">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c7462-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c7462-131">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c7462-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
