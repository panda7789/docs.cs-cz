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
ms.openlocfilehash: 82af06837ead9a00923c23d4ce145015308fbbf7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782807"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="4b1e3-102">ICorProfilerCallback::JITInlining – metoda</span><span class="sxs-lookup"><span data-stu-id="4b1e3-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="4b1e3-103">Oznámí profileru, že kompilátor just-in-time (JIT) Chystáte se vložit funkci v jiné funkci.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b1e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b1e3-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b1e3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4b1e3-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="4b1e3-106">[in] ID funkce, do kterého `calleeId` vloží funkce.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="4b1e3-107">[in] ID funkce má být vložen.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="4b1e3-108">[out] `true` vkládání dojde k; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b1e3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4b1e3-109">Remarks</span></span>  
 <span data-ttu-id="4b1e3-110">Profiler může nastavit `pfShouldInline` k `false` zabránit `calleeId` funkce nebude vložen do `callerId` funkce.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="4b1e3-111">Navíc můžete profiler globálně zakázat vložení vložené pomocí COR_PRF_DISABLE_INLINING hodnotu [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="4b1e3-112">Vložené funkce vloženy nevyvolávejte události pro zadání nebo byste museli opustit.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="4b1e3-113">Proto musíte nastavit profiler `pfShouldInline` k `false` cílem vytvořit přesný graf volání.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="4b1e3-114">Nastavení `pfShouldInline` k `false` ovlivní výkon, protože vložený vkládání obvykle zvyšuje rychlost a snižuje počet samostatných události kompilace JIT pro vložené metody.</span><span class="sxs-lookup"><span data-stu-id="4b1e3-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b1e3-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4b1e3-115">Requirements</span></span>  
 <span data-ttu-id="4b1e3-116">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b1e3-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b1e3-117">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4b1e3-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4b1e3-118">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b1e3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b1e3-119">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b1e3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b1e3-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4b1e3-120">See also</span></span>

- [<span data-ttu-id="4b1e3-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4b1e3-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
