---
title: ICorDebugModule – rozhraní
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
ms.openlocfilehash: 5fd8314c018653703a262c8c43e6113886c25047
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978680"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule – rozhraní

Představuje společný modul runtime (CLR) jazyk, který je spustitelný soubor nebo dynamická knihovna (DLL).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Není implementováno.|  
|[EnableClassLoadCallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Určuje, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) zpětná volání jsou volány pro tento modul.|  
|[EnableJITDebugging – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Určuje, zda kompilátor just-in-time (JIT) uchovává informace o ladění pro metody v rámci tohoto modulu.|  
|[GetAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Získá obsahující sestavení pro tento modul.|  
|[GetBaseAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Získá základní adresu modulu.|  
|[GetClassFromToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Získá ICorDebugClass z metadat.|  
|[GetEditAndContinueSnapshot – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Zastaralé|  
|[GetFunctionFromRVA – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Není implementováno.|  
|[GetFunctionFromToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Získá funkce, která je určená tokenem metadat.|  
|[GetGlobalVariableValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Získá objekt hodnoty pro zadaný globální proměnné.|  
|[GetMetaDataInterface – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Získá metadata ukazatel rozhraní, který lze použít pro přezkoumání metadat pro modul.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Získá název souboru modulu.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Získá nadřazený proces pro tento modul.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Získá velikost modulu v bajtech.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Získá token pro záznam tabulky pro tento modul.|  
|[IsDynamic – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Určuje, zda se jedná o dynamický modul.|  
|[IsInMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Označuje, zda tento modul existuje pouze v paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
