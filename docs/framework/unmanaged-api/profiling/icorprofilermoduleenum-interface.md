---
title: ICorProfilerModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: 5c4efff46c2460ee77f5a8011dc80796ac62a69e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442705"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekcí modulů načtených aplikací nebo profilerem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerModuleEnum`ho rozhraní.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Získá počet spravovaných modulů, které byly načteny do aplikace.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Získá zadaný počet souvislých modulů ze sekvenční kolekce objektů počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Přesune kurzor enumerátoru na počáteční pozici sekvence.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Posune pozici kurzoru enumerátoru tak, aby byl zadaný počet prvků vynechán.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorProfilerModuleEnum` je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModules – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
