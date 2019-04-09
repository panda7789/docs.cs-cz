---
title: ICorProfilerInfo5::SetEventMask2 – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 266219894ffefa0d4066c6ca68c7cadf6265e098
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175809"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="72937-102">ICorProfilerInfo5::SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="72937-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="72937-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="72937-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="72937-104">Nastaví hodnotu, která určuje typy událostí, pro které profileru chce obdržet oznámení událostí z common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="72937-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="72937-105">Nabízí víc funkcí než [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="72937-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72937-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72937-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72937-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="72937-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="72937-108">[in] 4 bajty. hodnota, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="72937-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="72937-109">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="72937-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="72937-110">Bity jsou popsány v [cor_prf_monitor –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="72937-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="72937-111">[in] 4 bajty. hodnota, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="72937-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="72937-112">Každý bit určuje různé možnosti, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="72937-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="72937-113">Bity jsou popsány v [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="72937-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72937-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72937-114">Remarks</span></span>  
 <span data-ttu-id="72937-115">`SetEventMask2` Metoda se používá k nastavení zpětná volání, ke kterým se přihlásí profileru.</span><span class="sxs-lookup"><span data-stu-id="72937-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="72937-116">Obvykle volání [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) metodou ke zjištění bity, které jsou nastaveny, provádět logický OR jeho `pdwEventsLow` a `pdwEventsHigh` hodnoty a všechny nové bity, které chcete nastavit a následně zavolat `SetEventMask2` metody.</span><span class="sxs-lookup"><span data-stu-id="72937-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="72937-117">Tato metoda je doporučenou alternativou k [seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="72937-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72937-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72937-118">Requirements</span></span>  
 <span data-ttu-id="72937-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72937-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72937-120">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72937-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72937-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72937-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="72937-122">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="72937-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="72937-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72937-123">See also</span></span>

- [<span data-ttu-id="72937-124">Rozhraní ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="72937-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="72937-125">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="72937-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
