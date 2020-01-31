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
ms.openlocfilehash: 655cdd5db0894a4e44d43b071caf1ee0829ffe50
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861720"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="e3c6b-102">Rozhraní ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="e3c6b-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="e3c6b-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e3c6b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e3c6b-104">Podtřída [ICorProfilerInfo4](icorprofilerinfo4-interface.md) , která poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí.</span><span class="sxs-lookup"><span data-stu-id="e3c6b-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3c6b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e3c6b-105">Methods</span></span>  
  
|<span data-ttu-id="e3c6b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e3c6b-106">Method</span></span>|<span data-ttu-id="e3c6b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e3c6b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3c6b-108">GetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e3c6b-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="e3c6b-109">Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z CLR.</span><span class="sxs-lookup"><span data-stu-id="e3c6b-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="e3c6b-110">SetEventMask2 – metoda</span><span class="sxs-lookup"><span data-stu-id="e3c6b-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="e3c6b-111">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení události z CLR.</span><span class="sxs-lookup"><span data-stu-id="e3c6b-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3c6b-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3c6b-112">Remarks</span></span>  
 <span data-ttu-id="e3c6b-113">Metody, které jsou k dispozici v tomto rozhraní, mají za cíl nahradit metody [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e3c6b-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c6b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e3c6b-114">Requirements</span></span>  
 <span data-ttu-id="e3c6b-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c6b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c6b-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e3c6b-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3c6b-117">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c6b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c6b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3c6b-118">See also</span></span>

- [<span data-ttu-id="e3c6b-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e3c6b-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
