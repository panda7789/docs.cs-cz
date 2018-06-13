---
title: ICorDebugModule Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule
helpviewer_keywords:
- ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db4a980929a644d2862a382f147505644313da7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422234"
---
# <a name="icordebugmodule-interface1"></a>ICorDebugModule Interface1
Představuje běžné modul runtime (CLR) jazyk, který je buď spustitelný soubor nebo dynamická knihovna (DLL).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Není implementováno.|  
|[EnableClassLoadCallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Určuje, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) pro tento modul se nazývají zpětných volání.|  
|[EnableJITDebugging – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.|  
|[GetAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Získá obsahující sestavení pro tento modul.|  
|[GetBaseAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Získá základní adresu modulu.|  
|[GetClassFromToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Získá ICorDebugClass z metadat.|  
|[GetEditAndContinueSnapshot – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Zastaralé|  
|[GetFunctionFromRVA – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Není implementováno.|  
|[GetFunctionFromToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Získá funkce, která je zadána token metadat.|  
|[GetGlobalVariableValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Získá objekt hodnoty pro zadaný globální proměnné.|  
|[GetMetaDataInterface – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Získá ukazatel rozhraní metadata, která můžete použít k prozkoumání metadata pro modul.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Získá název souboru modulu.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Získá obsahující proces pro tento modul.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Získá velikost modulu v bajtech.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Získá token pro položku tabulky pro tento modul.|  
|[IsDynamic – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Určuje, zda je modul dynamické.|  
|[IsInMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Určuje, zda tento modul existuje pouze v paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
