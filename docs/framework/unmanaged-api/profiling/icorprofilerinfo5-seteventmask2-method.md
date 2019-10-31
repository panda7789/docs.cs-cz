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
ms.openlocfilehash: 1e1779c0f4f36b2d7b81832bc90cf5aee0b8a7df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130394"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="ed1f9-102">ICorProfilerInfo5::SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ed1f9-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="ed1f9-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ed1f9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ed1f9-104">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce přijímat oznámení o událostech z modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ed1f9-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="ed1f9-105">Poskytuje více funkcí než metoda [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed1f9-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed1f9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed1f9-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed1f9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed1f9-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="ed1f9-108">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="ed1f9-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="ed1f9-109">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="ed1f9-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ed1f9-110">Bity jsou popsány ve výčtu [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ed1f9-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="ed1f9-111">pro Hodnota 4 bajtu, která určuje kategorie událostí.</span><span class="sxs-lookup"><span data-stu-id="ed1f9-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="ed1f9-112">Každý bit ovládá jinou schopnost, chování nebo typ události.</span><span class="sxs-lookup"><span data-stu-id="ed1f9-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="ed1f9-113">Bity jsou popsány ve výčtu [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ed1f9-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed1f9-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ed1f9-114">Remarks</span></span>  
 <span data-ttu-id="ed1f9-115">Metoda `SetEventMask2` slouží k nastavení zpětných volání, ke kterým se Profiler přihlašuje.</span><span class="sxs-lookup"><span data-stu-id="ed1f9-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="ed1f9-116">Obvykle zavoláte metodu [GetEventMask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a určíte, které bity jsou nastaveny, proveďte logický nebo jeho `pdwEventsLow` a `pdwEventsHigh` hodnoty a všechny nové bity, které chcete nastavit, a poté zavolejte metodu `SetEventMask2`.</span><span class="sxs-lookup"><span data-stu-id="ed1f9-116">Typically, you call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="ed1f9-117">Tato metoda je doporučená alternativou k metodě [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ed1f9-117">This method is the recommended alternative to the [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed1f9-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ed1f9-118">Requirements</span></span>  
 <span data-ttu-id="ed1f9-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed1f9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed1f9-120">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed1f9-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed1f9-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed1f9-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed1f9-122">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed1f9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed1f9-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed1f9-123">See also</span></span>

- [<span data-ttu-id="ed1f9-124">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ed1f9-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="ed1f9-125">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="ed1f9-125">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
