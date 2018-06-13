---
title: ICorProfilerCallback::JITInlining – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 844ac2a8aad4ce2cc6f70de2d5a53c7c0b6f4f6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453141"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="9794b-102">ICorProfilerCallback::JITInlining – metoda</span><span class="sxs-lookup"><span data-stu-id="9794b-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="9794b-103">Upozorní profileru, že kompilátoru v běhu (JIT) se chystáte vložit funkci souladu jinou funkci.</span><span class="sxs-lookup"><span data-stu-id="9794b-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9794b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9794b-104">Syntax</span></span>  
  
```  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9794b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9794b-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="9794b-106">[v] ID funkce, do kterého `calleeId` funkce bude možné vložit.</span><span class="sxs-lookup"><span data-stu-id="9794b-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="9794b-107">[v] ID funkce má být vložen.</span><span class="sxs-lookup"><span data-stu-id="9794b-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="9794b-108">[out] `true` vkládání dojít, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="9794b-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9794b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9794b-109">Remarks</span></span>  
 <span data-ttu-id="9794b-110">Můžete nastavit profileru `pfShouldInline` k `false` zabránit `calleeId` funkce z vkládání do `callerId` funkce.</span><span class="sxs-lookup"><span data-stu-id="9794b-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="9794b-111">Navíc můžete profileru globálně zakázat vložené vložení pomocí COR_PRF_DISABLE_INLINING hodnotu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="9794b-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="9794b-112">Vložené funkce Vložit není vyvolávání událostí pro zadání nebo ponechat.</span><span class="sxs-lookup"><span data-stu-id="9794b-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="9794b-113">Proto musíte nastavit profileru `pfShouldInline` k `false` Chcete-li vytvořit přesný callgraph.</span><span class="sxs-lookup"><span data-stu-id="9794b-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="9794b-114">Nastavení `pfShouldInline` k `false` ovlivní výkon, protože vložené vložení obvykle zvyšuje rychlost a snižuje počet samostatné událostí JIT kompilace pro metodu vložené.</span><span class="sxs-lookup"><span data-stu-id="9794b-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9794b-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9794b-115">Requirements</span></span>  
 <span data-ttu-id="9794b-116">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9794b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9794b-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9794b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9794b-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9794b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9794b-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9794b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9794b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9794b-120">See Also</span></span>  
 [<span data-ttu-id="9794b-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9794b-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
