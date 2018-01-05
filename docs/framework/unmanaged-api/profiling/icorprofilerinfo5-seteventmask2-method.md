---
title: "ICorProfilerInfo5::SetEventMask2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: IcorProfilerInfo5.SetEventMask2
api_location: mscorwks.dll
api_type: COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e53ad9d297656e26f8ba0e9d7669711a3f44ef1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="4e2c6-102">ICorProfilerInfo5::SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4e2c6-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="4e2c6-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="4e2c6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4e2c6-104">Nastaví hodnotu, která určuje typy událostí, pro které profileru chce dostávat oznámení o událostech, modul CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="4e2c6-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="4e2c6-105">Nabízí další funkce, než [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e2c6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e2c6-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e2c6-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="4e2c6-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="4e2c6-108">[v] 4bajtový hodnotu, která určuje kategorie události.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="4e2c6-109">Každý bit řídí jinou možnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="4e2c6-110">Službu bits, jsou popsané v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="4e2c6-111">[v] 4bajtový hodnotu, která určuje kategorie události.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="4e2c6-112">Každý bit řídí jinou možnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="4e2c6-113">Službu bits, jsou popsané v [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e2c6-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e2c6-114">Remarks</span></span>  
 <span data-ttu-id="4e2c6-115">`SetEventMask2` Metoda se používá k nastavení zpětná volání, do kterých profileru odběratel.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="4e2c6-116">Obvykle zavoláte [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metoda k určení, které bits jsou nastavené, provádět logickou funkcí nebo jeho `pdwEventsLow` a `pdwEventsHigh` hodnoty a všechny nové bitů, které chcete nastavit a pak zavolají `SetEventMask2` metoda.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="4e2c6-117">Tato metoda je Doporučená alternativa k [seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="4e2c6-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e2c6-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e2c6-118">Requirements</span></span>  
 <span data-ttu-id="4e2c6-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e2c6-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e2c6-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e2c6-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e2c6-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e2c6-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e2c6-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e2c6-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e2c6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e2c6-123">See Also</span></span>  
 [<span data-ttu-id="4e2c6-124">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4e2c6-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 [<span data-ttu-id="4e2c6-125">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="4e2c6-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
