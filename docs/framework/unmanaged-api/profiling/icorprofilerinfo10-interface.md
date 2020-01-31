---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863241"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 – rozhraní

Podtřída [ICorProfilerInfo9](icorprofilerinfo9-interface.md) , která poskytuje metody pro úpravu Il funkce, dotazování na informace z modulu runtime a pozastavení a obnovení modulu runtime.

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[Metoda EnumerateObjectReferences](icorprofilerinfo10-enumerateobjectreferences-method.md)|Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje). |
|[Metoda IsFrozenObject](icorprofilerinfo10-isfrozenobject-method.md)|V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení. |
|[Metoda GetLOHObjectSizeThreshold](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Získá hodnotu nakonfigurované prahové hodnoty LOH. |
|[Metoda RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md)| ReJITs požadované metody, jakož i všechny zažádané metody.  |
|[Metoda SuspendRuntime](icorprofilerinfo10-suspendruntime-method.md)| Pozastaví modul runtime bez provedení GC. |
|[Metoda ResumeRuntime](icorprofilerinfo10-resumeruntime-method.md)| Obnoví modul runtime bez provedení GC. |

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).  
**Hlavička:** CorProf. idl, CorProf. h  
**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
