---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 06cce79fbb2b2eb143e77e3c6fda194e47d4f4f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928792"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 – rozhraní

Podtřída [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) , která poskytuje metody pro úpravu Il funkce, dotazování na informace z modulu runtime a pozastavení a obnovení modulu runtime.

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[Metoda EnumerateObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje). |
|[Metoda IsFrozenObject](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení. |
|[Metoda GetLOHObjectSizeThreshold](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Získá hodnotu nakonfigurované prahové hodnoty LOH. |
|[Metoda RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs požadované metody, jakož i všechny zažádané metody.  |
|[Metoda SuspendRuntime](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| Pozastaví modul runtime bez provedení GC. |
|[Metoda ResumeRuntime](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| Obnoví modul runtime bez provedení GC. |

## <a name="requirements"></a>Požadavky  
**Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
**Hlaviček** CorProf.idl, CorProf.h  
**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
