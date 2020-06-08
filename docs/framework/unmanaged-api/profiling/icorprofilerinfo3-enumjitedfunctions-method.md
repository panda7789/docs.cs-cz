---
title: ICorProfilerInfo3::EnumJITedFunctions – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: 3ebf4a7706b3d3495e4a617b4f86a50281115436
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496552"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions – metoda
Vrátí enumerátor pro všechny funkce, které byly dříve kompilovány JIT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 mimo Ukazatel na enumerátor [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda se může překrývat s `JITCompilation` zpětnými voláními, jako je například metoda [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) . Enumerátor vrácený touto metodou nezahrnuje funkce, které jsou načteny z nativních imagí vygenerovaných pomocí nástroje Ngen. exe.  
  
> [!NOTE]
> Vrácený výčet obsahuje pro hodnotu pole pouze "0" `COR_PRF_FUNCTION::reJitId` .  Pokud požadujete platné `COR_PRF_FUNCTION::reJitId` hodnoty, použijte metodu [ICorProfilerInfo4:: EnumJITedFunctions2 –](icorprofilerinfo4-enumjitedfunctions2-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
