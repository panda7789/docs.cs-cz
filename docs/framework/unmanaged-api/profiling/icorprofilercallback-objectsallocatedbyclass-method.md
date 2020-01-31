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
ms.openlocfilehash: 028207486f43e35086ed2e515eb3ae6bca304491
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866070"
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
 pro Velikost polí `classIds` a `cObjects`  
  
 `classIds`  
 pro Pole identifikátorů třídy, kde každé ID určuje třídu s jednou nebo více instancemi.  
  
 `cObjects`  
 pro Pole celých čísel, kde každé celé číslo určuje počet instancí odpovídající třídy v poli `classIds`.  
  
## <a name="remarks"></a>Poznámky  
 Pole `classIds` a `cObjects` jsou paralelní pole. Například `classIds[i]` a `cObjects[i]` odkazují na stejnou třídu. Pokud nebyla od předchozího uvolňování paměti vytvořena žádná instance třídy, je třída vynechána. `ObjectsAllocatedByClass` zpětné volání nebude hlásit objekty přidělené v haldě velkých objektů.  
  
 Čísla uvedená `ObjectsAllocatedByClass` jsou pouze odhady. Pro přesné počty použijte [ICorProfilerCallback:: ObjectAllocated –](icorprofilercallback-objectallocated-method.md).  
  
 Pole `classIds` může obsahovat jednu nebo více položek s hodnotou null, pokud odpovídající pole `cObjects` obsahuje typy, které jsou uvolňovány.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
