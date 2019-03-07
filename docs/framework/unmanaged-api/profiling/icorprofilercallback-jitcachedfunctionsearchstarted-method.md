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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 526059e0895604d18025e8ad2fd037690243ff59
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503070"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda
Oznámí profileru, pro funkci, která se zkompilovala pomocí dříve Native Image Generator (NGen.exe) bylo zahájeno hledání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, pro které se provádí vyhledávání.  
  
 `pbUseCachedFunction`  
 [out] `true` pokud prováděcí modul by měl používat v mezipaměti verzi funkci (je-li k dispozici). v opačném `false`. Pokud je hodnota `false`, provádění modulu JIT zkompiluje funkci namísto použití verzi, která není kompilována JIT.  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 2.0 `JITCachedFunctionSearchStarted` a [icorprofilercallback::jitcachedfunctionsearchfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) zpětná volání, nebude možné zavést pro všechny funkce v běžných bitových kopií technologie NGen. Pouze obrázků NGen optimalizovaná pro profil, který vygeneruje zpětná volání pro všechny funkce v bitové kopii. Ale z důvodu další režie profileru by měl požádat o profileru optimalizované Image NGen pouze v případě, že to chce využít tato zpětná volání k vynucení funkce kompilované just-in-time (JIT). Profiler by jinak použijte opožděné strategie pro shromažďování informací funkce.  
  
 Profilovací programy musí podporovat případy, kdy více vláken profilované aplikace jsou volání stejné metody současně. Například, vlákna A zavolá `JITCachedFunctionSearchStarted` a profiler odpovídá nastavením *pbUseCachedFunction*na FALSE, pokud chcete vynutit kompilace JIT. Vlákna A poté zavolá [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) a [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Nyní vlákna volání B `JITCachedFunctionSearchStarted` pro stejnou funkci. I v případě, že profiler je uvedeno podat JIT-kompilovat funkci, profiler obdrží druhý zpětné volání, protože vlákno B odesílá zpětné volání před profiler reagoval na vlákno A volání `JITCachedFunctionSearchStarted`. Pořadí, ve kterém vlákna volání závisí na plánování vláken.  
  
 Když profiler obdrží duplicitní zpětná volání, je nutné nastavit hodnotu odkazuje `pbUseCachedFunction` na stejnou hodnotu pro duplicitní zpětná volání. To znamená, když `JITCachedFunctionSearchStarted` je se stejným názvem více než jednou `functionId` hodnotu, profiler musí odpovědět, stejné pokaždé, když.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
