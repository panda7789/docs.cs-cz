---
title: ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchFinished
helpviewer_keywords:
- JITCachedFunctionSearchFinished method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchFinished method [.NET Framework profiling]
ms.assetid: 3c325c82-cddd-4b00-b3da-e450c36abf62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0e78e10f092bce1c8f7762362f02b7a403c86a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597233"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchfinished-method"></a>ICorProfilerCallback::JITCachedFunctionSearchFinished – metoda
Upozornění profileru dokončení vyhledávání pro funkci, která se zkompilovala pomocí dříve Native Image Generator (NGen.exe).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT JITCachedFunctionSearchFinished(  
    [in] FunctionID        functionId,  
    [in] COR_PRF_JIT_CACHE result);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] ID funkce, pro který bylo hledání provedeno.  
  
 `result`  
 [in] Hodnota [cor_prf_jit_cache –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-jit-cache-enumeration.md) výčet, který určuje výsledek hledání.  
  
## <a name="remarks"></a>Poznámky  
 V rozhraní .NET Framework verze 2.0 [icorprofilercallback::jitcachedfunctionsearchstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md) a `JITCachedFunctionSearchFinished` zpětná volání, nebude možné zavést pro všechny funkce v běžných bitových kopií technologie NGen. Pouze obrázků NGen optimalizovaná pro profiler vygeneruje zpětná volání pro všechny funkce v bitové kopii. Ale z důvodu další režie profileru by měl požádat o profileru optimalizované Image NGen pouze v případě, že to chce využít tato zpětná volání k vynucení funkce kompilované just-in-time (JIT). Profiler by jinak použijte opožděné strategie pro shromažďování informací funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
