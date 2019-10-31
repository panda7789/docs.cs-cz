---
title: ICorDebugFunction3::GetActiveReJitRequestILCode – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugFunction3.GetActiveReJitRequestILCode
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type:
- apiref
ms.openlocfilehash: 0e706861237ed08700ef0abcc424b6f1de5f462c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134645"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatel rozhraní na [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppReJitedILCode`  
 Ukazatel na IL z aktivní žádosti ReJIT  
  
## <a name="remarks"></a>Poznámky  
 Pokud metoda reprezentovaná tímto objektem `ICorDebugFunction3` má aktivní požadavek ReJIT, `ppReJitedILCode` vrátí ukazatel na jeho IL. Pokud není žádná aktivní žádost, což je běžný případ, `ppReJitedILCode` je **null**.  
  
 Žádost ReJIT se aktivuje hned po návratu spuštění z volání metody [ICorProfilerCallback4:: GetReJITParameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) . Ještě nemusí být zkompilován kompilátorem JIT a vlákna mohou být stále spuštěna v původní verzi kódu. Požadavek ReJIT se v průběhu volání profileru do metody [ICorProfilerInfo4:: RequestRevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) přestanou neaktivní. I po vrácení IL se může vlákno i nadále spouštět v kódu ReJIT (JIT rekompilovaná).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugFunction3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ReJIT: Průvodce](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
