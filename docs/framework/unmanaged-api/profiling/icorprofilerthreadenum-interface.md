---
title: ICorProfilerThreadEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: b9fb308f19ff09218c97b030296b9a3d4f0f2512
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868184"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekcí vláken v modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](icorprofilerthreadenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerThreadEnum`ho rozhraní.|  
|[GetCount – metoda](icorprofilerthreadenum-getcount-method.md)|Získá počet vláken, která aplikace používá.|  
|[Next – metoda](icorprofilerthreadenum-next-method.md)|Získá zadaný počet souvislých vláken ze sekvenční kolekce vláken počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](icorprofilerthreadenum-reset-method.md)|Přesune kurzor enumerátoru na počáteční pozici sekvence.|  
|[Skip – metoda](icorprofilerthreadenum-skip-method.md)|Posune kurzor čítače výčtu z aktuální pozice pro přeskočení zadaného počtu prvků.|  
  
## <a name="remarks"></a>Poznámky  
 Rozhraní `ICorProfilerThreadEnum` je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
