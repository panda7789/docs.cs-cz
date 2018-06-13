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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2275eb37d0e62c3f0ee8bbc8ea6db66901a3f1c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458059"
---
# <a name="icorprofilermoduleenum-interface"></a>ICorProfilerModuleEnum – rozhraní
Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly zavedené aplikace nebo profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|Získá ukazatele rozhraní v kopii `ICorProfilerModuleEnum` rozhraní.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|Získá počet spravované moduly, které byly načteny do aplikace.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|Získá zadaný počet souvislý moduly z sekvenční kolekcí objektů, počínaje na enumerátor na aktuální pozici v pořadí.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|Posune kurzor enumerátor počáteční pozice pořadí.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|Přejde z pozice kurzoru enumerátor tak, aby se přeskočí zadaný počet elementů.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerModuleEnum` Rozhraní je enumerátor. Příjemce pole umožňuje na vyžádání elementy od odesílatele rychlostí, který je vhodný pro příjemce. Jinými slovy příjemce je schopen explicitně řízení toku prvků pole, aby se předešlo problémy spojené se předávání velké pole jako parametry metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumModules – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
