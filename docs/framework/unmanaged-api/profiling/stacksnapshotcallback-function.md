---
title: "StackSnapshotCallback – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 32cf21fb5a76fdec4daa322d53a8eb218ae2f2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stacksnapshotcallback-function"></a><span data-ttu-id="d3b50-102">StackSnapshotCallback – funkce</span><span class="sxs-lookup"><span data-stu-id="d3b50-102">StackSnapshotCallback Function</span></span>
<span data-ttu-id="d3b50-103">Poskytuje informace o každé spravované rámečkem a každé spuštění nespravované rámce v zásobníku při procházení zásobníku, který je inicializován nástrojem profileru [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="d3b50-103">Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3b50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3b50-104">Syntax</span></span>  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3b50-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3b50-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="d3b50-106">[v] Pokud je tato hodnota nulová, je tato zpětné volání pro spouštění funkce nespravované rámce; jinak je identifikátor spravované funkce a je tento zpětné volání pro spravované rámce.</span><span class="sxs-lookup"><span data-stu-id="d3b50-106">[in] If this value is zero, this callback is for a run of unmanaged frames; otherwise, it is the identifier of a managed function and this callback is for a managed frame.</span></span>  
  
 `ip`  
 <span data-ttu-id="d3b50-107">[v] Hodnota ukazatel instrukce nativního kódu v rámečku.</span><span class="sxs-lookup"><span data-stu-id="d3b50-107">[in] The value of the native code instruction pointer in the frame.</span></span>  
  
 `frameInfo`  
 <span data-ttu-id="d3b50-108">[v] A `COR_PRF_FRAME_INFO` hodnotu, která odkazuje na informace o rámce zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d3b50-108">[in] A `COR_PRF_FRAME_INFO` value that references information about the stack frame.</span></span> <span data-ttu-id="d3b50-109">Tato hodnota je platná pouze během této zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d3b50-109">This value is valid for use only during this callback.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="d3b50-110">[v] Velikost `CONTEXT` strukturu, která odkazuje `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="d3b50-110">[in] The size of the `CONTEXT` structure, which is referenced by the `context` parameter.</span></span>  
  
 `context`  
 <span data-ttu-id="d3b50-111">[v] Ukazatel na Win32 `CONTEXT` struktura, která představuje stav procesoru pro tento snímek.</span><span class="sxs-lookup"><span data-stu-id="d3b50-111">[in] A pointer to a Win32 `CONTEXT` structure that represents the state of the CPU for this frame.</span></span>  
  
 <span data-ttu-id="d3b50-112">`context` Parametr je platný pouze v případě, že byla předána příznak COR_PRF_SNAPSHOT_CONTEXT `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="d3b50-112">The `context` parameter is valid only if the COR_PRF_SNAPSHOT_CONTEXT flag was passed in `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d3b50-113">[v] Ukazatel na klienta data, která je předána přímo z `ICorProfilerInfo2::DoStackSnapshot`.</span><span class="sxs-lookup"><span data-stu-id="d3b50-113">[in] A pointer to the client data, which is passed straight through from `ICorProfilerInfo2::DoStackSnapshot`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3b50-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3b50-114">Remarks</span></span>  
 <span data-ttu-id="d3b50-115">`StackSnapshotCallback` Funkce je implementována pro zápis profileru.</span><span class="sxs-lookup"><span data-stu-id="d3b50-115">The `StackSnapshotCallback` function is implemented by the profiler writer.</span></span> <span data-ttu-id="d3b50-116">Je nutné omezit složitosti práci `StackSnapshotCallback`.</span><span class="sxs-lookup"><span data-stu-id="d3b50-116">You must limit the complexity of work done in `StackSnapshotCallback`.</span></span> <span data-ttu-id="d3b50-117">Například při použití `ICorProfilerInfo2::DoStackSnapshot` v asynchronním režimu, může být cílový vlákno podržíte zámky.</span><span class="sxs-lookup"><span data-stu-id="d3b50-117">For example, when using `ICorProfilerInfo2::DoStackSnapshot` in an asynchronous manner, the target thread may be holding locks.</span></span> <span data-ttu-id="d3b50-118">Pokud kódu v rámci `StackSnapshotCallback` vyžaduje stejné zámků, by mohly vzájemné zablokování.</span><span class="sxs-lookup"><span data-stu-id="d3b50-118">If code within `StackSnapshotCallback` requires the same locks, a deadlock could ensue.</span></span>  
  
 <span data-ttu-id="d3b50-119">`ICorProfilerInfo2::DoStackSnapshot` Volání metod `StackSnapshotCallback` funkce jednou za spravované snímek nebo jednou za spuštění nespravované rámce.</span><span class="sxs-lookup"><span data-stu-id="d3b50-119">The `ICorProfilerInfo2::DoStackSnapshot` method calls the `StackSnapshotCallback` function once per managed frame or once per run of unmanaged frames.</span></span> <span data-ttu-id="d3b50-120">Pokud `StackSnapshotCallback` je volána pro běh nespravované rámce, může použít profileru kontext registrace (odkazuje `context` parametr) k provedení vlastní procházení nespravované zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d3b50-120">If `StackSnapshotCallback` is called for a run of unmanaged frames, the profiler may use the register context (referenced by the `context` parameter) to perform its own unmanaged stack walk.</span></span> <span data-ttu-id="d3b50-121">V tomto případě Win32 `CONTEXT` struktura představuje stav procesoru pro nedávno stisknutí rámečku v rámci spustit nespravované snímků.</span><span class="sxs-lookup"><span data-stu-id="d3b50-121">In this case, the Win32 `CONTEXT` structure represents the CPU state for the most recently pushed frame within the run of unmanaged frames.</span></span> <span data-ttu-id="d3b50-122">I když Win32 `CONTEXT` struktura zahrnuje hodnoty pro všechny registrů, spoléhat na hodnoty registru ukazatel zásobníku, rámec ukazatel registru, registrace ukazatel instrukce a permanentní (ke které se zachovají) zaregistruje celé číslo.</span><span class="sxs-lookup"><span data-stu-id="d3b50-122">Although the Win32 `CONTEXT` structure includes values for all registers, you should rely only on the values of the stack pointer register, frame pointer register, instruction pointer register, and the nonvolatile (that is, preserved) integer registers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3b50-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3b50-123">Requirements</span></span>  
 <span data-ttu-id="d3b50-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3b50-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b50-125">**Záhlaví:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="d3b50-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d3b50-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3b50-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3b50-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3b50-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3b50-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3b50-128">See Also</span></span>  
 [<span data-ttu-id="d3b50-129">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="d3b50-129">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="d3b50-130">Globální statické funkce pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d3b50-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
