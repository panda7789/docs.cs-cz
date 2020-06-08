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
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496123"
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
 Tato metoda se může překrývat s `JITCompilation` zpětnými voláními, jako je například metoda [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) . Vrácený výčet obsahuje hodnoty pro `COR_PRF_FUNCTION::reJitId` pole. Metoda [ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) , kterou tato metoda nahrazuje, nevytváří výčet ID rekompilovaných JIT JIT, protože `COR_PRF_FUNCTION::reJitId` pole je vždy nastaveno na hodnotu 0. `ICorProfilerInfo4::EnumJITedFunctions`Metoda provede výčet rekompilovaných identifikátorů JIT, protože `COR_PRF_FUNCTION::reJitId` pole je nastaveno správně. Všimněte si, že metoda [ICorProfilerInfo4:: EnumJITedFunctions2 –](icorprofilerinfo4-enumjitedfunctions2-method.md) může aktivovat uvolňování paměti, zatímco [Metoda ICorProfilerInfo3:: EnumJITedFunctions –](icorprofilerinfo3-enumjitedfunctions-method.md) nebude.  Další informace najdete v tématu [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EnumJITedFunctions – metoda](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 – rozhraní](icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
