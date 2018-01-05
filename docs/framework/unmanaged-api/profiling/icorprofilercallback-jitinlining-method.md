---
title: "ICorProfilerCallback::JITInlining – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITInlining
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3990fdf1bcf76592288aac35b47b15f42cf77bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="322a0-102">ICorProfilerCallback::JITInlining – metoda</span><span class="sxs-lookup"><span data-stu-id="322a0-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="322a0-103">Upozorní profileru, že kompilátoru v běhu (JIT) se chystáte vložit funkci souladu jinou funkci.</span><span class="sxs-lookup"><span data-stu-id="322a0-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="322a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="322a0-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="322a0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="322a0-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="322a0-106">[v] ID funkce, do kterého `calleeId` funkce bude možné vložit.</span><span class="sxs-lookup"><span data-stu-id="322a0-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="322a0-107">[v] ID funkce má být vložen.</span><span class="sxs-lookup"><span data-stu-id="322a0-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="322a0-108">[out] `true` vkládání dojít, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="322a0-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="322a0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="322a0-109">Remarks</span></span>  
 <span data-ttu-id="322a0-110">Můžete nastavit profileru `pfShouldInline` k `false` zabránit `calleeId` funkce z vkládání do `callerId` funkce.</span><span class="sxs-lookup"><span data-stu-id="322a0-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="322a0-111">Navíc můžete profileru globálně zakázat vložené vložení pomocí COR_PRF_DISABLE_INLINING hodnotu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="322a0-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="322a0-112">Vložené funkce Vložit není vyvolávání událostí pro zadání nebo ponechat.</span><span class="sxs-lookup"><span data-stu-id="322a0-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="322a0-113">Proto musíte nastavit profileru `pfShouldInline` k `false` Chcete-li vytvořit přesný callgraph.</span><span class="sxs-lookup"><span data-stu-id="322a0-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="322a0-114">Nastavení `pfShouldInline` k `false` ovlivní výkon, protože vložené vložení obvykle zvyšuje rychlost a snižuje počet samostatné událostí JIT kompilace pro metodu vložené.</span><span class="sxs-lookup"><span data-stu-id="322a0-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="322a0-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="322a0-115">Requirements</span></span>  
 <span data-ttu-id="322a0-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="322a0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="322a0-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="322a0-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="322a0-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="322a0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="322a0-119">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="322a0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322a0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="322a0-120">See Also</span></span>  
 [<span data-ttu-id="322a0-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="322a0-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
