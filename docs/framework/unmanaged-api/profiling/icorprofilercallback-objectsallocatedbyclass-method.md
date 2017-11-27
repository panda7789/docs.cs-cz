---
title: "ICorProfilerCallback::ObjectsAllocatedByClass – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ObjectsAllocatedByClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 28c0ff537a5b2133bdeb1db8aeadf5545d8dfd0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass – metoda
Informuje o počtu instancí každé zadané třídy, které byly vytvořeny od poslední uvolňování profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cClassCount`  
 [v] Velikost `classIds` a `cObjects` pole.  
  
 `classIds`  
 [v] Pole ID, kde každý ID Určuje třídu s jednu nebo více instancí tříd.  
  
 `cObjects`  
 [v] Pole celých čísel, kde každý celé číslo určuje počet instancí pro odpovídající třídu v `classIds` pole.  
  
## <a name="remarks"></a>Poznámky  
 `classIds` a `cObjects` pole jsou paralelní pole. Například `classIds[i]` a `cObjects[i]` odkazovat na stejnou třídu. Pokud od předchozí uvolňování byla vytvořena žádná instance třídy, třída je vynechán. `ObjectsAllocatedByClass` Zpětného volání, nebudou podávat objekty přidělené v haldě velkého objektu.  
  
 Čísla hlášené `ObjectsAllocatedByClass` jsou jenom odhadované. Pro přesné počty použít [icorprofilercallback::objectallocated –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md).  
  
 `classIds` Pole může obsahovat jeden nebo více položky s hodnotou null, pokud odpovídající `cObjects` pole obsahuje typy, které jsou uvolnění.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
