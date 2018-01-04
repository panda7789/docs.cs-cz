---
title: "Výčet COR_PRF_HIGH_MONITOR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 3ba543d8-15e5-4322-b6e7-1ebfc92ed7dd
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ec30d19af133b4f0734dadf8775dc8682666e22
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfhighmonitor-enumeration"></a><span data-ttu-id="d5eb8-102">Výčet COR_PRF_HIGH_MONITOR</span><span class="sxs-lookup"><span data-stu-id="d5eb8-102">COR_PRF_HIGH_MONITOR Enumeration</span></span>
<span data-ttu-id="d5eb8-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="d5eb8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="d5eb8-104">Poskytuje příznaky kromě těch, které v nalezen [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčet, který můžete vybrat profileru [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metoda při jeho načítání.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-104">Provides flags in addition to those found in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration that the profiler can specify to the [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method when it is loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5eb8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5eb8-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_HIGH_MONITOR_NONE                = 0x00000000,  
    COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES     = 0x00000001,  
    COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED     = 0x00000002,     
    COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE       = 0,  
    COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH      = COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED,  
    COR_PRF_HIGH_MONITOR_IMMUTABLE           = 0  
} COR_PRF_HIGH_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="d5eb8-106">Členové</span><span class="sxs-lookup"><span data-stu-id="d5eb8-106">Members</span></span>  
  
|<span data-ttu-id="d5eb8-107">Člen</span><span class="sxs-lookup"><span data-stu-id="d5eb8-107">Member</span></span>|<span data-ttu-id="d5eb8-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d5eb8-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_HIGH_MONITOR_NONE`|<span data-ttu-id="d5eb8-109">Žádné příznaky se nastavují.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-109">No flags are set.</span></span>|  
|`COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES`|<span data-ttu-id="d5eb8-110">Ovládací prvky [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání pro přidání odkazů na sestavení během procházení uzavření odkaz na sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-110">Controls the [ICorProfilerCallback6::GetAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback for adding assembly references during the CLR assembly reference closure walk.</span></span>|  
|`COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED`|<span data-ttu-id="d5eb8-111">Ovládací prvky [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) zpětné volání pro aktualizace do datového proudu symbol, který je přidružený modul v paměti.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-111">Controls the [ICorProfilerCallback7::ModuleInMemorySymbolsUpdated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md) callback for updates to the symbol stream associated with an in-memory module.</span></span>|  
|`COR_PRF_HIGH_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="d5eb8-112">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které vyžadují rozšířené profil bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-112">Represents all `COR_PRF_HIGH_MONITOR` flags that require profile-enhanced images.</span></span> <span data-ttu-id="d5eb8-113">Odpovídá `COR_PRF_REQUIRE_PROFILE_IMAGE` příznak v [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) výčtu.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-113">It corresponds to the `COR_PRF_REQUIRE_PROFILE_IMAGE` flag in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>|  
|`COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="d5eb8-114">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit po profileru k spuštěné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-114">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span>|  
|`COR_PRF_HIGH_MONITOR_IMMUTABLE`|<span data-ttu-id="d5eb8-115">Představuje všechny `COR_PRF_HIGH_MONITOR` příznaky, které lze nastavit pouze během inicializace.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-115">Represents all `COR_PRF_HIGH_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="d5eb8-116">Pokusu změnit tyto příznaky jinde vede `HRESULT` hodnotu, která určuje selhání.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-116">Trying to change any of these flags elsewhere results in an `HRESULT` value that indicates failure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5eb8-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5eb8-117">Remarks</span></span>  
 <span data-ttu-id="d5eb8-118">`COR_PRF_HIGH_MONITOR` Příznaky, které se používají s `pdwEventsHigh` parametr [icorprofilerinfo5::geteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) a [icorprofilerinfo5::seteventmask2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="d5eb8-118">The `COR_PRF_HIGH_MONITOR` flags are used with the `pdwEventsHigh` parameter of the [ICorProfilerInfo5::GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) and [ICorProfilerInfo5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) methods.</span></span>  
  
 <span data-ttu-id="d5eb8-119">Od verze [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], hodnota `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` změnit od 0 do `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span><span class="sxs-lookup"><span data-stu-id="d5eb8-119">Starting with the [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)], the value of the `COR_PRF_HIGH_ALLOWABLE_AFTER_ATTACH` changed from 0 to `COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED` (0x00000002).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5eb8-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5eb8-120">Requirements</span></span>  
 <span data-ttu-id="d5eb8-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5eb8-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5eb8-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d5eb8-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d5eb8-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5eb8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5eb8-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5eb8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5eb8-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5eb8-125">See Also</span></span>  
 [<span data-ttu-id="d5eb8-126">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d5eb8-126">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 [<span data-ttu-id="d5eb8-127">COR_PRF_MONITOR – výčet</span><span class="sxs-lookup"><span data-stu-id="d5eb8-127">COR_PRF_MONITOR Enumeration</span></span>](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)  
 [<span data-ttu-id="d5eb8-128">ICorProfilerInfo5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d5eb8-128">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
