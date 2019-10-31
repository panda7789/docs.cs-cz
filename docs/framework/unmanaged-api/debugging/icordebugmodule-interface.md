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
ms.openlocfilehash: 971d6a6a2157c48dcb9105e9f523b1f077098479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129485"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule – rozhraní

Představuje modul modulu CLR (Common Language Runtime), což je spustitelný soubor nebo knihovna DLL (Dynamic-Link Library).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Není implementováno.|  
|[EnableClassLoadCallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Určuje, zda jsou pro tento modul volána zpětná volání [ICorDebugManagedCallback:: LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) .|  
|[EnableJITDebugging – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Určuje, zda kompilátor JIT (just-in-time) zachovává ladicí informace pro metody v rámci tohoto modulu.|  
|[GetAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Získá nadřazené sestavení pro tento modul.|  
|[GetBaseAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Získá základní adresu modulu.|  
|[GetClassFromToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Získá ICorDebugClass z metadat.|  
|[GetEditAndContinueSnapshot – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Zastaralé|  
|[GetFunctionFromRVA – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Není implementováno.|  
|[GetFunctionFromToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Získá funkci, která je určena tokenem metadat.|  
|[GetGlobalVariableValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Získá objekt hodnoty pro zadanou globální proměnnou.|  
|[GetMetaDataInterface – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Získá ukazatel rozhraní metadat, který lze použít k prohlédnutí metadat pro modul.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Získá název souboru modulu.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Získá obsahující proces pro tento modul.|  
|[GetSize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Získá velikost modulu v bajtech.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Získá token pro položku tabulky pro tento modul.|  
|[IsDynamic – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Určuje, zda je modul dynamický.|  
|[IsInMemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Určuje, zda tento modul existuje pouze v paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
