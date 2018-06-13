---
title: Výčet COR_PRF_HIGH_MONITOR
ms.date: 04/10/2018
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92ba2b5eac5eb1368a7d7ccf3b666886f4ca92a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454711"
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="7e73d-102">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="7e73d-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="7e73d-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="7e73d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7e73d-104">Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.</span><span class="sxs-lookup"><span data-stu-id="7e73d-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e73d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e73d-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                     = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES          = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED        = 0x00000002,     
    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS = 0x00000004,    
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE            = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH           = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | 
                                                    COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE                = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="7e73d-106">Členové</span><span class="sxs-lookup"><span data-stu-id="7e73d-106">Members</span></span>  
  
|<span data-ttu-id="7e73d-107">Člen</span><span class="sxs-lookup"><span data-stu-id="7e73d-107">Member</span></span>|<span data-ttu-id="7e73d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7e73d-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="7e73d-109">Žádné příznaky se nastavují.</span><span class="sxs-lookup"><span data-stu-id="7e73d-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="7e73d-110">Ovládací prvky [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání pro přidání odkazů na sestavení během procházení uzavření odkaz na sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="7e73d-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="7e73d-111">Ovládací prvky [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětné volání pro aktualizace do datového proudu symbol, který je přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="7e73d-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`|<span data-ttu-id="7e73d-112">Ovládací prvky [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) zpětné volání pro označující při dynamické metoda byla paměti shromážděných a odpojeno.</span><span class="sxs-lookup"><span data-stu-id="7e73d-112">Controls the [ICorProfilerCallback9::DynamicMethodUnloaded](icorprofilercallback9-dynamicmethodunloaded-method.md) callback for indicating when a dynamic method has been garbage collected and unloaded.</span></span> <br/> [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]|   
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="7e73d-113">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které vyžadují rozšířené profil bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="7e73d-113">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="7e73d-114">Odpovídá `COR_PRF_REQUIRE_PROFILE_IMAGE` příznak v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="7e73d-114">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="7e73d-115">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit po profileru k spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7e73d-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="7e73d-116">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="7e73d-116">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="7e73d-117">Pokusu změnit tyto příznaky jinde vede `HRESULT` hodnotu, která určuje selhání.</span><span class="sxs-lookup"><span data-stu-id="7e73d-117">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e73d-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e73d-118">Remarks</span></span>  
 <span data-ttu-id="7e73d-119">`COR_PRF_HIGH_MONITOR` Příznaky, které se používají s `pdwEventsHigh` parametr [icorprofilerinfo5::geteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7e73d-119">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
<span data-ttu-id="7e73d-120">Od verze [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změnit od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="7e73d-120">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span> <span data-ttu-id="7e73d-121">Od verze rozhraní .NET Framework 4.7.2, jeho hodnota změněna z `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` k `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span><span class="sxs-lookup"><span data-stu-id="7e73d-121">Starting with the .NET Framework 4.7.2, its value changed from `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED | COR_PRF_HIGH_MONITOR_DYNAMIC_FUNCTION_UNLOADS`.</span></span>   

<span data-ttu-id="7e73d-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` má být bitová maska, která představuje všechny příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="7e73d-122">`COR_PRF_HIGH_MONITOR_IMMUTABLE` is intended to be a bitmask that represents all flags that can only be set during initialization.</span></span> <span data-ttu-id="7e73d-123">Při pokusu o změnit tyto příznaky jinde výsledkem nezdařené `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7e73d-123">Trying to change any of these flags elsewhere results in a failed `HRESULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e73d-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7e73d-124">Requirements</span></span>  
 <span data-ttu-id="7e73d-125">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e73d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e73d-126">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e73d-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e73d-127">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e73d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e73d-128">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e73d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e73d-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e73d-129">See Also</span></span>  
 [<span data-ttu-id="7e73d-130">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7e73d-130">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [<span data-ttu-id="7e73d-131">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="7e73d-131">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [<span data-ttu-id="7e73d-132">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7e73d-132">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
