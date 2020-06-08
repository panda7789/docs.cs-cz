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
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500010"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="9d6d8-102">ICorProfilerCallback::JITInlining – metoda</span><span class="sxs-lookup"><span data-stu-id="9d6d8-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="9d6d8-103">Upozorní profileru, že kompilátor JIT (just-in-time) se chystá Vložit funkci do řádku s jinou funkcí.</span><span class="sxs-lookup"><span data-stu-id="9d6d8-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6d8-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d6d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d6d8-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="9d6d8-106">pro ID funkce, do které `calleeId` bude vložena funkce</span><span class="sxs-lookup"><span data-stu-id="9d6d8-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="9d6d8-107">pro ID funkce, která má být vložena.</span><span class="sxs-lookup"><span data-stu-id="9d6d8-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="9d6d8-108">[out] `true` aby bylo možné vložení provést; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="9d6d8-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d6d8-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d6d8-109">Remarks</span></span>  
 <span data-ttu-id="9d6d8-110">Profiler může nastavit, `pfShouldInline` aby `false` zabránil `calleeId` Vložení funkce do `callerId` funkce.</span><span class="sxs-lookup"><span data-stu-id="9d6d8-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="9d6d8-111">Profiler může také globálně zakázat vložené vložení pomocí COR_PRF_DISABLE_INLINING hodnoty výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="9d6d8-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="9d6d8-112">Funkce vložené vložením nevyvolávají události pro vložení nebo ukončení.</span><span class="sxs-lookup"><span data-stu-id="9d6d8-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="9d6d8-113">Proto musí Profiler nastavit na, `pfShouldInline` aby `false` vytvořil přesný graf volání.</span><span class="sxs-lookup"><span data-stu-id="9d6d8-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="9d6d8-114">Nastavení `pfShouldInline` na `false` bude mít vliv na výkon, protože vložené vložení obvykle zvyšuje rychlost a snižuje počet samostatných událostí kompilace JIT pro vloženou metodu.</span><span class="sxs-lookup"><span data-stu-id="9d6d8-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6d8-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d6d8-115">Requirements</span></span>  
 <span data-ttu-id="9d6d8-116">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6d8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6d8-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d6d8-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d6d8-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9d6d8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d6d8-119">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6d8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d6d8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d6d8-120">See also</span></span>

- [<span data-ttu-id="9d6d8-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d6d8-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
