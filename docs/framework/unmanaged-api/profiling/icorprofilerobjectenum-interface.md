---
title: ICorProfilerObjectEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
ms.openlocfilehash: 95dce47a65bd437525011d2c1588d7e13adac85b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428187"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekce zmrazených objektů, které jsou generovány pomocí nástroje [Ngen. exe (generátor nativních imagí)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerObjectEnum`ho rozhraní.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Získá celkový počet zmrazených objektů v kolekci.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Získá zadaný počet souvislých objektů ze sekvenční kolekce objektů počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Přesune ukazatel tohoto čítače výčtu na počáteční pozici sekvence.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Přesune kurzor tohoto čítače z aktuální pozice tak, aby byl zadaný počet prvků vynechán.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorProfilerObjectEnum` je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
 K získání ukazatele na `ICorProfilerObjectEnum` rozhraní použijte [ICorProfilerInfo2:: EnumModuleFrozenObjects –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModuleFrozenObjects – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
