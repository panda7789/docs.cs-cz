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
ms.openlocfilehash: 5ebe99dd8d1d7ec73cd140991a4b13dfa381791d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494641"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekce zmrazených objektů, které jsou generovány pomocí nástroje [Ngen. exe (generátor nativních imagí)](../../tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Clone – metoda](icorprofilerobjectenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerObjectEnum` rozhraní.|  
|[GetCount – metoda](icorprofilerobjectenum-getcount-method.md)|Získá celkový počet zmrazených objektů v kolekci.|  
|[Next – metoda](icorprofilerobjectenum-next-method.md)|Získá zadaný počet souvislých objektů ze sekvenční kolekce objektů počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](icorprofilerobjectenum-reset-method.md)|Přesune ukazatel tohoto čítače výčtu na počáteční pozici sekvence.|  
|[Skip – metoda](icorprofilerobjectenum-skip-method.md)|Přesune kurzor tohoto čítače z aktuální pozice tak, aby byl zadaný počet prvků vynechán.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerObjectEnum`Rozhraní je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
 K získání ukazatele na rozhraní použijte [ICorProfilerInfo2:: EnumModuleFrozenObjects –](icorprofilerinfo2-enummodulefrozenobjects-method.md) `ICorProfilerObjectEnum` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [EnumModuleFrozenObjects – metoda](icorprofilerinfo2-enummodulefrozenobjects-method.md)
