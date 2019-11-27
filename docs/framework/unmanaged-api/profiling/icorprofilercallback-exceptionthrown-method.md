---
title: ICorProfilerCallback::ExceptionThrown – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: 4ecbe0ef3c3021c5633b9380da2eb31cf22aa4b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445323"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a>ICorProfilerCallback::ExceptionThrown – metoda
Upozorní profileru, že byla vyvolána výjimka.  
  
> [!NOTE]
> Tato funkce je volána pouze v případě, že výjimka dosáhne spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a>Parametry  
 `thrownObjectId`  
 pro ID objektu, který způsobil výjimku vyvolání výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Profiler by neměl při implementaci této metody blokovat, protože zásobník pravděpodobně není ve stavu, který umožňuje uvolňování paměti, a proto nelze povolit bezstavové uvolňování paměti. Pokud se tady zablokuje Profiler a dojde k pokusu o uvolnění paměti, modul runtime se zablokuje, dokud toto zpětné volání nevrátí.  
  
 Implementace této metody v profileru by se neměla volat do spravovaného kódu nebo jakýmkoli způsobem způsobovat alokaci spravované paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
