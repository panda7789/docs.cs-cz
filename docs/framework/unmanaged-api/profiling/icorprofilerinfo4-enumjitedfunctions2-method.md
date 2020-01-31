---
title: ICorProfilerInfo4::EnumJITedFunctions2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862201"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 – metoda
Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT a rekompilovány JIT. Tato metoda nahrazuje metodu [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) , která neprovádí výčet znovu kompilovaných ID JIT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 mimo Ukazatel na enumerátor [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se může překrývat s `JITCompilation`mi zpětnými voláními, jako je například metoda [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) . Vrácený výčet obsahuje hodnoty pro pole `COR_PRF_FUNCTION::reJitId`. Metoda [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) , kterou tato metoda nahrazuje, nevytváří výčet ID rekompilovaných JIT JIT, protože pole `COR_PRF_FUNCTION::reJitId` je vždy nastaveno na hodnotu 0. Metoda `ICorProfilerInfo4::EnumJITedFunctions` provede výčet rekompilovaných identifikátorů JIT, protože pole `COR_PRF_FUNCTION::reJitId` je nastavené správně. Všimněte si, že metoda [ICorProfilerInfo4:: EnumJITedFunctions2 –](icorprofilerinfo4-enumjitedfunctions2-method.md) může aktivovat uvolňování paměti, zatímco [Metoda ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) nebude.  Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EnumJITedFunctions – metoda](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
