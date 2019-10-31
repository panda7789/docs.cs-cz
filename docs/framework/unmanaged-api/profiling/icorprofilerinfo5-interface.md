---
title: Rozhraní ICorProfilerInfo5
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo5
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 7bd48c34-37ed-4230-9eec-39a17280f05d
topic_type:
- apiref
ms.openlocfilehash: e6df5dcb26d61d30407d1efeeed7d207744276fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124190"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="5b87d-102">Rozhraní ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="5b87d-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="5b87d-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="5b87d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="5b87d-104">Podtřída [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , která poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí.</span><span class="sxs-lookup"><span data-stu-id="5b87d-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b87d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5b87d-105">Methods</span></span>  
  
|<span data-ttu-id="5b87d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5b87d-106">Method</span></span>|<span data-ttu-id="5b87d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5b87d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b87d-108">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5b87d-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="5b87d-109">Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z CLR.</span><span class="sxs-lookup"><span data-stu-id="5b87d-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="5b87d-110">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="5b87d-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="5b87d-111">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení události z CLR.</span><span class="sxs-lookup"><span data-stu-id="5b87d-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b87d-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b87d-112">Remarks</span></span>  
 <span data-ttu-id="5b87d-113">Metody, které jsou k dispozici v tomto rozhraní, mají za cíl nahradit metody [ICorProfilerInfo:: GetEventMask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5b87d-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b87d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b87d-114">Requirements</span></span>  
 <span data-ttu-id="5b87d-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b87d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b87d-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5b87d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b87d-117">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b87d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b87d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b87d-118">See also</span></span>

- [<span data-ttu-id="5b87d-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="5b87d-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
