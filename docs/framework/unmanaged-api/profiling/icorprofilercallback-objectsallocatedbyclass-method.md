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
ms.openlocfilehash: 7176c0f88daad64f793131aca8c6d9fa592a878c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503273"
---
# <a name="icorprofilercallbackobjectsallocatedbyclass-method"></a>ICorProfilerCallback::ObjectsAllocatedByClass – metoda
Upozorňuje Profiler o počtu instancí každé zadané třídy, které byly vytvořeny od posledního uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ObjectsAllocatedByClass(  
    [in] ULONG   cClassCount,  
    [in, size_is(cClassCount)] ClassID classIds[] ,  
    [in, size_is(cClassCount)] ULONG   cObjects[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cClassCount`  
 pro Velikost `classIds` `cObjects` polí a.  
  
 `classIds`  
 pro Pole identifikátorů třídy, kde každé ID určuje třídu s jednou nebo více instancemi.  
  
 `cObjects`  
 pro Pole celých čísel, kde každé celé číslo určuje počet instancí odpovídající třídy v `classIds` poli.  
  
## <a name="remarks"></a>Poznámky  
 Pole `classIds` a `cObjects` jsou paralelní pole. Například `classIds[i]` a `cObjects[i]` odkazovat na stejnou třídu. Pokud nebyla od předchozího uvolňování paměti vytvořena žádná instance třídy, je třída vynechána. `ObjectsAllocatedByClass`Zpětné volání nebude hlásit objekty, které jsou přiděleny v haldě velkých objektů.  
  
 Čísla uvedená v rámci `ObjectsAllocatedByClass` jsou pouze odhadovaná. Pro přesné počty použijte [ICorProfilerCallback:: ObjectAllocated –](icorprofilercallback-objectallocated-method.md).  
  
 `classIds`Pole může obsahovat jednu nebo více položek s hodnotou null, pokud odpovídající `cObjects` pole obsahuje typy, které jsou uvolňovány.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
