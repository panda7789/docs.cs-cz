---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 30179c7c198a343baa3fa01ae64f6d580a3f9e7e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452198"
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
**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
**Hlavička:** CorProf. idl, CorProf. h  
**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)] 

## <a name="see-also"></a>Viz také

- [Rozhraní pro profilaci](profiling-interfaces.md)
