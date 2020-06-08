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
ms.openlocfilehash: 82f6262c2c576b49be4e7fcaa14043950df4c67a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495624"
---
# <a name="icorprofilerinfo5-interface"></a><span data-ttu-id="300d1-102">Rozhraní ICorProfilerInfo5</span><span class="sxs-lookup"><span data-stu-id="300d1-102">ICorProfilerInfo5 Interface</span></span>
<span data-ttu-id="300d1-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="300d1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="300d1-104">Podtřída [ICorProfilerInfo4](icorprofilerinfo4-interface.md) , která poskytuje metody pro použití v profilech kódu ke komunikaci s modulem CLR (Common Language Runtime) pro řízení sledování událostí.</span><span class="sxs-lookup"><span data-stu-id="300d1-104">A subclass of [ICorProfilerInfo4](icorprofilerinfo4-interface.md) that provides methods for use by code profilers to communicate with the common language runtime (CLR) to control event monitoring.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="300d1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="300d1-105">Methods</span></span>  
  
|<span data-ttu-id="300d1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="300d1-106">Method</span></span>|<span data-ttu-id="300d1-107">Description</span><span class="sxs-lookup"><span data-stu-id="300d1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="300d1-108">Metoda GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="300d1-108">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)|<span data-ttu-id="300d1-109">Získá aktuální kategorie událostí, pro které profiler chce dostávat oznámení z CLR.</span><span class="sxs-lookup"><span data-stu-id="300d1-109">Gets the current event categories for which the profiler wants to receive notifications from the CLR.</span></span>|  
|[<span data-ttu-id="300d1-110">Metoda SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="300d1-110">SetEventMask2 Method</span></span>](icorprofilerinfo5-seteventmask2-method.md)|<span data-ttu-id="300d1-111">Nastaví hodnotu, která určuje typy událostí, pro které profiler chce dostávat oznámení události z CLR.</span><span class="sxs-lookup"><span data-stu-id="300d1-111">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the CLR.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="300d1-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="300d1-112">Remarks</span></span>  
 <span data-ttu-id="300d1-113">Metody, které jsou k dispozici v tomto rozhraní, mají za cíl nahradit metody [ICorProfilerInfo:: GetEventMask –](icorprofilerinfo-geteventmask-method.md) a [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="300d1-113">The methods available on this interface are intended to replace the [ICorProfilerInfo::GetEventMask](icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="300d1-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="300d1-114">Requirements</span></span>  
 <span data-ttu-id="300d1-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="300d1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="300d1-116">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="300d1-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="300d1-117">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="300d1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300d1-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="300d1-118">See also</span></span>

- [<span data-ttu-id="300d1-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="300d1-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
