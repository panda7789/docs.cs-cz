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
ms.openlocfilehash: fe11c0bbe273ae07cdae43f681a558e07a291ffb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494888"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekcí modulů načtených aplikací nebo profilerem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Clone – metoda](icorprofilermoduleenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerModuleEnum` rozhraní.|  
|[GetCount – metoda](icorprofilermoduleenum-getcount-method.md)|Získá počet spravovaných modulů, které byly načteny do aplikace.|  
|[Next – metoda](icorprofilermoduleenum-next-method.md)|Získá zadaný počet souvislých modulů ze sekvenční kolekce objektů počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](icorprofilermoduleenum-reset-method.md)|Přesune kurzor enumerátoru na počáteční pozici sekvence.|  
|[Skip – metoda](icorprofilermoduleenum-skip-method.md)|Posune pozici kurzoru enumerátoru tak, aby byl zadaný počet prvků vynechán.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerModuleEnum`Rozhraní je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [EnumModules – metoda](icorprofilerinfo3-enummodules-method.md)
