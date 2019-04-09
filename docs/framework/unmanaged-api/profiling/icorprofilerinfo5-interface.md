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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b249605833e8fbd219495ab92bebc2eff6177eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094252"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="7fbd2-102">Rozhraní ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="7fbd2-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="7fbd2-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="7fbd2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7fbd2-104">Podtřída [icorprofilerinfo4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) , který poskytuje metody pro použití u profilery kódu ke komunikaci s common language runtime (CLR) k řízení, monitorování událostí.</span><span class="sxs-lookup"><span data-stu-id="7fbd2-104">A subclass of [ICorProfilerInfo4](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fbd2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7fbd2-105">Methods</span></span>  
  
|<span data-ttu-id="7fbd2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7fbd2-106">Method</span></span>|<span data-ttu-id="7fbd2-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7fbd2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fbd2-108">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7fbd2-108">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="7fbd2-109">Získá aktuální kategorie událostí, pro které profileru chce, aby dostávala oznámení z modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7fbd2-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="7fbd2-110">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="7fbd2-110">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="7fbd2-111">Nastaví hodnotu, která určuje typy událostí, pro které profileru chce obdržet oznámení událostí z modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="7fbd2-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fbd2-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fbd2-112">Remarks</span></span>  
 <span data-ttu-id="7fbd2-113">Metody dostupné pro tato rozhraní jsou určeny k nahrazení [icorprofilerinfo::geteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7fbd2-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fbd2-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7fbd2-114">Requirements</span></span>  
 <span data-ttu-id="7fbd2-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fbd2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fbd2-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7fbd2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="7fbd2-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7fbd2-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7fbd2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fbd2-118">See also</span></span>

- [<span data-ttu-id="7fbd2-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7fbd2-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
