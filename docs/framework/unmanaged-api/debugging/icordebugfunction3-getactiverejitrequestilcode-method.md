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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af101e8d842c20394816a3408c74709da941bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a>ICorDebugFunction3::GetActiveReJitRequestILCode – metoda
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Získá ukazatele rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) obsahující IL z active ReJIT žádosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppReJitedILCode`  
 Ukazatel na IL z active ReJIT žádosti.  
  
## <a name="remarks"></a>Poznámky  
 Pokud metodu reprezentovanou tímto objektem `ICorDebugFunction3` objekt má požadavek active ReJIT `ppReJitedILCode` vrací ukazatel na jeho IL. Pokud neexistuje žádné aktivní požadavku, což je běžně, pak `ppReJitedILCode` je **null**.  
  
 Žádost o ReJIT stane aktivní jenom po provedení vrátí z [icorprofilercallback4::getrejitparameters –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) volání metody. Ještě nemusí být kompilována a vláken může být stále provádí v původní verzi kód. Během volání profileru se stane neaktivní žádost ReJIT [icorprofilerinfo4::requestrevert –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metoda. I po IL je vrátit zpět, vlákno můžete stále provádí v kódu překompilovat JIT (ReJIT).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugFunction3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [ReJIT: Postupy: Průvodce](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
