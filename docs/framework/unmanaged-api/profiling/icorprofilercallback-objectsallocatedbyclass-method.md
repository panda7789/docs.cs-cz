---
title: ICorProfilerCallback::ObjectsAllocatedByClass – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectsAllocatedByClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectsAllocatedByClass
helpviewer_keywords:
- ObjectsAllocatedByClass method [.NET Framework profiling]
- ICorProfilerCallback::ObjectsAllocatedByClass method [.NET Framework profiling]
ms.assetid: 91d688f3-a80e-419d-9755-ff94bc04188a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 78dde5c50666333c02c8c1a9a167e17af3f40341
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
