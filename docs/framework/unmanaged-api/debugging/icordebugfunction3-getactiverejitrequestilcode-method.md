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
ms.openlocfilehash: 9e7f682752cfefae63b574655a4fc5e8964146a0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213176"
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode – metoda
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatel rozhraní na [ICorDebugILCode](icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.  
  
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
 Pokud metoda reprezentovaná tímto `ICorDebugFunction3` objektem má aktivní požadavek ReJIT, `ppReJitedILCode` vrátí ukazatel na jeho Il. Pokud neexistuje žádná aktivní žádost, což je běžný případ, `ppReJitedILCode` je **hodnota null**.  
  
 Žádost ReJIT se aktivuje hned po návratu spuštění z volání metody [ICorProfilerCallback4:: GetReJITParameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) . Ještě nemusí být zkompilován kompilátorem JIT a vlákna mohou být stále spuštěna v původní verzi kódu. Požadavek ReJIT se v průběhu volání profileru do metody [ICorProfilerInfo4:: RequestRevert –](../profiling/icorprofilerinfo4-requestrevert-method.md) přestanou neaktivní. I po vrácení IL se může vlákno i nadále spouštět v kódu ReJIT (JIT rekompilovaná).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugFunction3](icordebugfunction3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [ReJIT: Průvodce](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
