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
ms.openlocfilehash: 6d97b40412b6999000a601b72904a03edf2acd08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454030"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a>ICorProfilerCallback::JITCachedFunctionSearchStarted – metoda
Aby bylo zahájeno hledání pro funkce, který byl kompilován s použitím dříve generátor (NGen.exe) upozorní profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 [v] ID funkce, pro které se provádí vyhledávání.  
  
 `pbUseCachedFunction`  
 [out] `true` jestli modul provádění by neměl používat v mezipaměti verze funkce (Pokud je k dispozici); jinak `false`. Pokud je hodnota `false`, provádění modul JIT zkompiluje funkce místo použití na verzi, která není kompilována.  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 2.0 `JITCachedFunctionSearchStarted` a [icorprofilercallback::jitcachedfunctionsearchfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) zpětná volání nebude možné vytvořit pro všechny funkce v pravidelných NGen bitové kopie. Pouze NGen obrázky optimalizované pro profil vygeneruje zpětných volání pro všechny funkce v bitové kopii. Však z důvodu další režie profileru měli požádat o optimalizované profileru obrazy NGen pouze v případě, že má v úmyslu použít tyto zpětná volání, které vynutí funkce, která má být kompilované v běhu (JIT). Profileru, jinak hodnota by měla použít opožděné strategie pro shromažďování informací funkce.  
  
 Profilery musí podporovat případy, kdy několik vláken PROFILOVANÉHO aplikace jsou volání stejnou metodu současně. Například přístup z více vláken A volá `JITCachedFunctionSearchStarted` a profileru odpovídá nastavením *pbUseCachedFunction*na hodnotu FALSE, chcete-li vynutit JIT – kompilace. Přístup z více vláken potom volá [icorprofilercallback::jitcompilationstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) a [icorprofilercallback::jitcompilationfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).  
  
 Nyní vláken B volání `JITCachedFunctionSearchStarted` pro stejnou funkci. I když profileru má uvádí svůj záměr JIT – kompilace funkce, profileru obdrží druhý zpětného volání, protože vlákno B odesílá zpětné volání, než profileru reagoval na vlákno na volání `JITCachedFunctionSearchStarted`. Pořadí, ve kterém vláken volání závisí na tom, jak jsou naplánovány vláken.  
  
 Když profileru obdrží duplicitní zpětná volání, je nutné nastavit hodnotu odkazuje `pbUseCachedFunction` na stejnou hodnotu pro všechny duplicitní zpětných volání. To znamená, že pokud `JITCachedFunctionSearchStarted` je volat vícekrát, se stejným `functionId` hodnotu, profileru musí odpovědět, stejné pokaždé, když.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
