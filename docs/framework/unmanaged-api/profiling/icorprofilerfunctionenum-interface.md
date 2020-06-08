---
title: ICorProfilerFunctionEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: b69afa7676ad174725f13c1113ff3bd9972995f8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503078"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum – rozhraní
Poskytuje metody pro sekvenční iteraci kolekcí funkcí v modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[Clone – metoda](icorprofilerfunctionenum-clone-method.md)|Získá ukazatel rozhraní na kopii tohoto `ICorProfilerFunctionEnum` rozhraní.|  
|[GetCount – metoda](icorprofilerfunctionenum-getcount-method.md)|Získá počet funkcí, které byly načteny aplikací nebo vynuceně načteny profilerem.|  
|[Next – metoda](icorprofilerfunctionenum-next-method.md)|Získá zadaný počet souvislých funkcí z sekvenční kolekce funkcí počínaje aktuální pozicí čítače výčtu v sekvenci.|  
|[Reset – metoda](icorprofilerfunctionenum-reset-method.md)|Přesune kurzor enumerátoru na počáteční pozici sekvence.|  
|[Skip – metoda](icorprofilerfunctionenum-skip-method.md)|Posune kurzor čítače výčtu z aktuální pozice tak, aby byl zadaný počet prvků vynechán.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerFunctionEnum`Rozhraní je enumerátor. Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce. Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.  
  
 `ICorProfilerFunctionEnum`Vytvoří výčet pro funkce, které již byly kompilovány JIT, ale nezahrnuje funkce, které jsou načteny z nativních imagí vygenerovaných pomocí nástroje Ngen. exe.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [EnumJITedFunctions – metoda](icorprofilerinfo3-enumjitedfunctions-method.md)
