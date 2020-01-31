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
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866208"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="078ce-102">ICorProfilerCallback::JITInlining – metoda</span><span class="sxs-lookup"><span data-stu-id="078ce-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="078ce-103">Upozorní profileru, že kompilátor JIT (just-in-time) se chystá Vložit funkci do řádku s jinou funkcí.</span><span class="sxs-lookup"><span data-stu-id="078ce-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="078ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="078ce-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="078ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="078ce-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="078ce-106">pro ID funkce, do které bude vložena funkce `calleeId`.</span><span class="sxs-lookup"><span data-stu-id="078ce-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="078ce-107">pro ID funkce, která má být vložena.</span><span class="sxs-lookup"><span data-stu-id="078ce-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="078ce-108">[out] `true`, pokud chcete, aby bylo vkládání provedeno; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="078ce-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="078ce-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="078ce-109">Remarks</span></span>  
 <span data-ttu-id="078ce-110">Profiler může nastavit `pfShouldInline` `false`, aby se zabránilo vložení funkce `calleeId` do `callerId` funkce.</span><span class="sxs-lookup"><span data-stu-id="078ce-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="078ce-111">Profiler může také globálně zakázat vložené vložení pomocí COR_PRF_DISABLE_INLINING hodnoty výčtu [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="078ce-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="078ce-112">Funkce vložené vložením nevyvolávají události pro vložení nebo ukončení.</span><span class="sxs-lookup"><span data-stu-id="078ce-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="078ce-113">Proto musí Profiler nastavit `pfShouldInline`, aby `false`, aby vytvořil přesný graf volání.</span><span class="sxs-lookup"><span data-stu-id="078ce-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="078ce-114">Nastavení `pfShouldInline` `false` bude mít vliv na výkon, protože vložené vložení obvykle zvyšuje rychlost a snižuje počet samostatných událostí kompilace JIT pro vloženou metodu.</span><span class="sxs-lookup"><span data-stu-id="078ce-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="078ce-115">Požadavky</span><span class="sxs-lookup"><span data-stu-id="078ce-115">Requirements</span></span>  
 <span data-ttu-id="078ce-116">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="078ce-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="078ce-117">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="078ce-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="078ce-118">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="078ce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="078ce-119">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="078ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="078ce-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="078ce-120">See also</span></span>

- [<span data-ttu-id="078ce-121">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="078ce-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
