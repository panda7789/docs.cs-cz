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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: df3baf21de7a1e6ec0590d85719eaa40d5da489f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54511901"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum – rozhraní
Poskytuje metody pro postupně iteraci prostřednictvím kolekce funkcí v modulu common language runtime.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Získá ukazatel rozhraní na kopii této `ICorProfilerFunctionEnum` rozhraní.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Získá počet funkcí, které byly načteny aplikací nebo vynuceně načíst pomocí profileru.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Získá zadaný počet souvislých funkce z sekvenční kolekce funkcí, od aktuální pozice čítače výčtu v sekvenci.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Přesune kurzor čítače výčtu na počáteční pozici pořadí.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Posune kurzor enumerátor z aktuálního umístění tak, aby zadaný počet prvků, které se přeskočí.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerFunctionEnum` Rozhraní je enumerátor. Umožňuje příjemce pole prvků o přijetí změn od odesílatele rychlostí, která je vhodná pro příjemce. Jinými slovy příjemce je explicitně řídit tok prvků pole, aby se předešlo problémy související s předání velkých polí jako parametrů metody.  
  
 `ICorProfilerFunctionEnum` Vytvoří výčet prostřednictvím funkcí, které již byly zkompilovány JIT, ale neobsahuje funkce, které jsou načteny z nativní bitové kopie generované nástrojem Ngen.exe.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
