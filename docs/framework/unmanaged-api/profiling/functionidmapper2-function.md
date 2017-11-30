---
title: "FunctionIDMapper2 – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionIDMapper2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionIDMapper2
helpviewer_keywords: FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5da0acdd7622ad06879b57d8d4b2a9faeba10ca9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="functionidmapper2-function"></a><span data-ttu-id="9629f-102">FunctionIDMapper2 – funkce</span><span class="sxs-lookup"><span data-stu-id="9629f-102">FunctionIDMapper2 Function</span></span>
<span data-ttu-id="9629f-103">Profileru upozorní, že daným identifikátorem funkce může namapovat na alternativní ID, které má být používány [functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), a [functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), nebo[functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), a [functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) zpětných volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="9629f-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function.</span></span> <span data-ttu-id="9629f-104">`FunctionIDMapper2`taky umožňuje profileru indikující, zda chce dostávat zpětných volání pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="9629f-104">`FunctionIDMapper2` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9629f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9629f-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9629f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9629f-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="9629f-107">[v] Identifikátor funkce přemapování.</span><span class="sxs-lookup"><span data-stu-id="9629f-107">[in] The function identifier to be remapped.</span></span>  
  
 `clientData`  
 <span data-ttu-id="9629f-108">[v] Ukazatel na data, která se používá k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="9629f-108">[in] A pointer to data that is used to disambiguate among runtimes.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="9629f-109">[out] Ukazatel na hodnotu, která nastaví profileru `true` Pokud chce dostávat `FunctionEnter3`, `FunctionLeave3`, a `FunctionTailcall3`, nebo `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, a `FunctionTailcall3WithInfo` zpětná volání; jinak, nastaví této hodnoty na `false`.</span><span class="sxs-lookup"><span data-stu-id="9629f-109">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter3`, `FunctionLeave3`, and `FunctionTailcall3`, or `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, and `FunctionTailcall3WithInfo` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9629f-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9629f-110">Return Value</span></span>  
 <span data-ttu-id="9629f-111">Profileru vrátí hodnotu, která modul provádění používá jako identifikátor alternativní funkce.</span><span class="sxs-lookup"><span data-stu-id="9629f-111">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="9629f-112">Návratová hodnota nemůže být null. Pokud `false` je vrácený v `pbHookFunction`.</span><span class="sxs-lookup"><span data-stu-id="9629f-112">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="9629f-113">Návratovou hodnotou null, jinak hodnota vytvoří nepředvídatelné výsledky včetně pravděpodobně zastavení procesu.</span><span class="sxs-lookup"><span data-stu-id="9629f-113">Otherwise, a null return value produces unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9629f-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9629f-114">Remarks</span></span>  
 <span data-ttu-id="9629f-115">Tato metoda rozšiřuje [functionidmapper –](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkce s dalším parametrem, který slouží k předávání dat klienta.</span><span class="sxs-lookup"><span data-stu-id="9629f-115">This method extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with an additional parameter that is used to pass client data.</span></span> <span data-ttu-id="9629f-116">Data klienta se používá k rozlišení mezi moduly runtime.</span><span class="sxs-lookup"><span data-stu-id="9629f-116">The client data is used to disambiguate among runtimes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9629f-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9629f-117">Requirements</span></span>  
 <span data-ttu-id="9629f-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9629f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9629f-119">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="9629f-119">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9629f-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9629f-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9629f-121">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9629f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9629f-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9629f-122">See Also</span></span>  
 [<span data-ttu-id="9629f-123">Icorprofilerinfo::setfunctionidmapper –</span><span class="sxs-lookup"><span data-stu-id="9629f-123">ICorProfilerInfo::SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="9629f-124">Icorprofilerinfo3::setfunctionidmapper2 –</span><span class="sxs-lookup"><span data-stu-id="9629f-124">ICorProfilerInfo3::SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="9629f-125">Functionenter3 –</span><span class="sxs-lookup"><span data-stu-id="9629f-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="9629f-126">Functionleave3 –</span><span class="sxs-lookup"><span data-stu-id="9629f-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="9629f-127">Functiontailcall3 –</span><span class="sxs-lookup"><span data-stu-id="9629f-127">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="9629f-128">Functionenter3withinfo –</span><span class="sxs-lookup"><span data-stu-id="9629f-128">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="9629f-129">Functionleave3withinfo –</span><span class="sxs-lookup"><span data-stu-id="9629f-129">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="9629f-130">Functiontailcall3withinfo –</span><span class="sxs-lookup"><span data-stu-id="9629f-130">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="9629f-131">Profilace globálních statických funkcí</span><span class="sxs-lookup"><span data-stu-id="9629f-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
