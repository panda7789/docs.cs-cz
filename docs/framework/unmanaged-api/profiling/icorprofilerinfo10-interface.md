---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175067"
---
# <a name="icorprofilerinfo10-interface"></a>ICorProfilerInfo10 – rozhraní

Podtřída [ICorProfilerInfo9,](icorprofilerinfo9-interface.md) která poskytuje metody pro úpravu funkce IL, informace o dotazu z běhu a pozastavení a obnovení běhu.

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[EnumerateObjectReferences – metoda](icorprofilerinfo10-enumerateobjectreferences-method.md)|Dané ObjectID, zpětné volání a clientData, vyjmenovává každý odkaz na objekt (pokud existuje). |
|[IsFrozenObject – metoda](icorprofilerinfo10-isfrozenobject-method.md)|Dané ObjectID, určuje, zda je objekt v segmentu jen pro čtení. |
|[GetLOHObjectSizeThreshold – metoda](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|Získá hodnotu nakonfigurované prahové hodnoty LOH. |
|[RequestReJITWithInliners – metoda](icorprofilerinfo10-requestrejitwithinliners-method.md)| Požadované metody, jakož i všechny vložky požadovaných metod.  |
|[SuspendRuntime – metoda](icorprofilerinfo10-suspendruntime-method.md)| Pozastaví dobu běhu bez provedení gc. |
|[ResumeRuntime – metoda](icorprofilerinfo10-resumeruntime-method.md)| Obnoví dobu běhu bez provedení gc. |

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [operační systémy podporované rozhraním .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
**Záhlaví:** CorProf.idl, CorProf.h  
**Verze rozhraní .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>Viz také

- [Rozhraní pro profilaci](profiling-interfaces.md)
