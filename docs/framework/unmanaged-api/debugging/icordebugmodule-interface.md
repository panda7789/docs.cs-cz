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
ms.openlocfilehash: 105e56f2508eabbb6876a09d35e6abfbfc08950b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212240"
---
# <a name="icordebugmodule-interface"></a>ICorDebugModule – rozhraní

Představuje modul modulu CLR (Common Language Runtime), což je spustitelný soubor nebo knihovna DLL (Dynamic-Link Library).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CreateBreakpoint – metoda](icordebugmodule-createbreakpoint-method.md)|Není implementováno.|  
|[EnableClassLoadCallbacks – metoda](icordebugmodule-enableclassloadcallbacks-method.md)|Určuje, zda jsou pro tento modul volána zpětná volání [ICorDebugManagedCallback:: LoadClass –](icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](icordebugmanagedcallback-unloadclass-method.md) .|  
|[EnableJITDebugging – metoda](icordebugmodule-enablejitdebugging-method.md)|Určuje, zda kompilátor JIT (just-in-time) zachovává ladicí informace pro metody v rámci tohoto modulu.|  
|[GetAssembly – metoda](icordebugmodule-getassembly-method.md)|Získá nadřazené sestavení pro tento modul.|  
|[GetBaseAddress – metoda](icordebugmodule-getbaseaddress-method.md)|Získá základní adresu modulu.|  
|[GetClassFromToken – metoda](icordebugmodule-getclassfromtoken-method.md)|Získá ICorDebugClass z metadat.|  
|[GetEditAndContinueSnapshot – metoda](icordebugmodule-geteditandcontinuesnapshot-method.md)|Zastaralé|  
|[GetFunctionFromRVA – metoda](icordebugmodule-getfunctionfromrva-method.md)|Není implementováno.|  
|[GetFunctionFromToken – metoda](icordebugmodule-getfunctionfromtoken-method.md)|Získá funkci, která je určena tokenem metadat.|  
|[GetGlobalVariableValue – metoda](icordebugmodule-getglobalvariablevalue-method.md)|Získá objekt hodnoty pro zadanou globální proměnnou.|  
|[GetMetaDataInterface – metoda](icordebugmodule-getmetadatainterface-method.md)|Získá ukazatel rozhraní metadat, který lze použít k prohlédnutí metadat pro modul.|  
|[GetName – metoda](icordebugmodule-getname-method.md)|Získá název souboru modulu.|  
|[GetProcess – metoda](icordebugmodule-getprocess-method.md)|Získá obsahující proces pro tento modul.|  
|[GetSize – metoda](icordebugmodule-getsize-method.md)|Získá velikost modulu v bajtech.|  
|[GetToken – metoda](icordebugmodule-gettoken-method.md)|Získá token pro položku tabulky pro tento modul.|  
|[IsDynamic – metoda](icordebugmodule-isdynamic-method.md)|Určuje, zda je modul dynamický.|  
|[IsInMemory – metoda](icordebugmodule-isinmemory-method.md)|Určuje, zda tento modul existuje pouze v paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebug – rozhraní](icordebug-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
