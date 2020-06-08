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
ms.openlocfilehash: d28991254fba73de7a55135844d16417580d8792
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494381"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekcí vláken v modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Clone – metoda](icorprofilerthreadenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerThreadEnum` rozhraní.|  
|[GetCount – metoda](icorprofilerthreadenum-getcount-method.md)|Získá počet vláken, která aplikace používá.|  
|[Next – metoda](icorprofilerthreadenum-next-method.md)|Získá zadaný počet souvislých vláken ze sekvenční kolekce vláken počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](icorprofilerthreadenum-reset-method.md)|Přesune kurzor enumerátoru na počáteční pozici sekvence.|  
|[Skip – metoda](icorprofilerthreadenum-skip-method.md)|Posune kurzor čítače výčtu z aktuální pozice pro přeskočení zadaného počtu prvků.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerThreadEnum`Rozhraní je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
