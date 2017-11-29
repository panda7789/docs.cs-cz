---
title: "ICorProfilerObjectEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum
helpviewer_keywords: ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b46f33485a63404f11dc0606e420ec9c3c43f1f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum – rozhraní
Poskytuje metody pro postupně iteraci přes kolekci ukotvené objektů, které jsou generované [Ngen.exe (Generátor nativních obrázků)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|Získá ukazatele rozhraní v kopii `ICorProfilerObjectEnum` rozhraní.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|Získá celkový počet ukotvené objektů v kolekci.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|Získá zadaný počet souvislý objektů z sekvenční kolekcí objektů, počínaje na enumerátor na aktuální pozici v pořadí.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|Přesune tento enumerátor kurzor na počáteční pozice pořadí.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|Posune kurzor tento enumerátoru z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorProfilerObjectEnum` Rozhraní je enumerátor. Příjemce pole umožňuje na vyžádání elementy od odesílatele rychlostí, který je vhodný pro příjemce. Jinými slovy příjemce je schopen explicitně řízení toku prvků pole, aby se předešlo problémy související s předávání velké pole jako parametry metody.  
  
 Použití [ICorProfilerInfo2::enummodulefrozenobjects –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md) k získání ukazatele na `ICorProfilerObjectEnum` rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Enummodulefrozenobjects – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
