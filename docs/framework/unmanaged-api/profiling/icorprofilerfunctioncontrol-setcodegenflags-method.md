---
title: ICorProfilerFunctionControl::SetCodegenFlags – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: 75414ec3d2b30fe8afc5db1e97c81f34b29a3115
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864671"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags – metoda
Nastaví jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) pro řízení generování kódu pro rekompilován funkci just-in-time (JIT).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 pro Jeden nebo více příznaků z výčtu [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Profiler získá instanci tohoto rozhraní prostřednictvím zpětného volání [ICorProfilerCallback4:: GetReJITParameters –](icorprofilercallback4-getrejitparameters-method.md) . `SetCodegenFlags` umožňuje profileru řídit generování kódu pro rekompilovaný funkce. Stejně jako všechny ostatní parametry rekompilace JIT se příznaky generování kódu vztahují na všechny instance funkce.  
  
 Kompilátor JIT považuje tyto příznaky kompilace společně s dalšími příznaky určenými jinými zdroji při kompilování funkce.  Mezi ostatní zdroje patří ladicí program, globální příznaky nastavené profilerem při spuštění pomocí metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) (s hodnotami `COR_PRF_DISABLE_INLINING` a `COR_PRF_DISABLE_OPTIMIZATIONS`) a zpětným voláním [ICorProfilerCallback:: JITInlining –](icorprofilercallback-jitinlining-method.md) profileru.  Kompilátor JIT dává přednost zdroji, který požaduje nejmenší množství optimalizace.  Například pokud profiler určí `COR_PRF_DISABLE_INLINING` při spuštění, ale neurčí `COR_PRF_CODEGEN_DISABLE_INLINING` ve zpětném volání [ICorProfilerFunctionControl:: SetCodegenFlags –](icorprofilerfunctioncontrol-setcodegenflags-method.md) , vkládání je stále zakázáno.  Podobně platí, že pokud profiler neurčí `COR_PRF_CODEGEN_DISABLE_INLINING` v `SetCodegenFlags`, ale zakáže vkládání pomocí zpětného volání [ICorProfilerCallback:: JITInlining –](icorprofilercallback-jitinlining-method.md) , vkládání je zakázané.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerFunctionControl – rozhraní](icorprofilerfunctioncontrol-interface.md)
