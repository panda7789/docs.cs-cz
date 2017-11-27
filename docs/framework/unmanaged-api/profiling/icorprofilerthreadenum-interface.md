---
title: "ICorProfilerThreadEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum
helpviewer_keywords: ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2ce48c836070018059becd1ece269ce7c878c7ba
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum – rozhraní
Poskytuje metody pro postupně iteraci prostřednictvím kolekce vláken v modulu CLR.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|Získá ukazatele rozhraní v kopii `ICorProfilerThreadEnum` rozhraní.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|Získá počet vláken, které používají aplikace.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|Získá zadaný počet vláken, souvislý z kolekce sekvenčních vláken, začínající na enumerátor na aktuální pozici v pořadí.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|Posune kurzor enumerátor počáteční pozice pořadí.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|Posune kurzor enumerátor z aktuálního umístění tak, aby přeskočil zadaný počet elementů.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerThreadEnum` Rozhraní je enumerátor. Příjemce pole umožňuje na vyžádání elementy od odesílatele rychlostí, který je vhodný pro příjemce. Jinými slovy příjemce je schopen explicitně řízení toku prvků pole, aby se předešlo problémy spojené se předávání velké pole jako parametry metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilerinfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
