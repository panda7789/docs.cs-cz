---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: d8f4a04abea0bd5eb9bf38629a8fcaf76479bcc9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500053"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda
Upozorní profileru, že pro funkci, která byla dříve kompilována pomocí generátoru nativních imagí (NGen. exe), bylo spuštěno vyhledávání.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parametry

- `functionId`

  \[v] ID funkce, pro kterou je prováděno hledání.

- `pbUseCachedFunction`

  \[out], `true` Pokud má spouštěcí modul používat verzi funkce uložené v mezipaměti (Pokud je k dispozici). v opačném případě `false` . Pokud je hodnota `false` , prováděcí modul JIT – zkompiluje funkci namísto použití verze, která není kompilována JIT.

## <a name="remarks"></a>Poznámky  
 V .NET Framework verze 2,0 `JITCachedFunctionSearchStarted` nebudou zpětná volání [metod a ICorProfilerCallback:: jitcachedfunctionsearchfinished –](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) pro všechny funkce v normálních bitových kopiích Ngen provedeny. Zpětná volání pro všechny funkce v imagi budou generovat pouze image NGen optimalizované pro profil. V důsledku dodatečné režie by měl Profiler vyžádat image NGen optimalizované profilerem jenom v případě, že má v úmyslu použít tato zpětná volání k vynucení funkce JIT just-in-time (JIT). V opačném případě by Profiler měl používat opožděnou strategii pro shromažďování informací o funkcích.  
  
 Profilery musí podporovat případy, kdy více vláken profilované aplikace volá stejnou metodu současně. Například vlákno a `JITCachedFunctionSearchStarted` Profiler odpoví nastavením *pbUseCachedFunction*na hodnotu false pro vynucení kompilace JIT. Vlákno A potom zavolá [ICorProfilerCallback:: JITCompilationStarted –](icorprofilercallback-jitcompilationstarted-method.md) a [ICorProfilerCallback:: JITCompilationFinished –](icorprofilercallback-jitcompilationfinished-method.md).  
  
 Nyní vlákno B volá `JITCachedFunctionSearchStarted` stejnou funkci. I když Profiler uvedl svůj úmysl na kompilaci funkce JIT, Profiler obdrží druhé zpětné volání, protože vlákno B odesílá zpětné volání předtím, než Profiler odpoví na volání Thread A `JITCachedFunctionSearchStarted` . Pořadí, ve kterém vlákna volají, závisí na tom, jak jsou vlákna naplánována.  
  
 Když Profiler obdrží duplicitní zpětná volání, musí nastavit hodnotu, na kterou odkazuje, `pbUseCachedFunction` na stejnou hodnotu pro všechna duplicitní zpětná volání. To znamená, že pokud `JITCachedFunctionSearchStarted` je vyvolána vícekrát se stejnou `functionId` hodnotou, musí Profiler vždy odpovědět na stejnou hodnotu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
