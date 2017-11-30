---
title: ICorDebugModule Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule
helpviewer_keywords: ICorDebugModule interface [.NET Framework debugging]
ms.assetid: 32e4d6fa-e5a3-413e-9166-d5e2871d3114
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ced01c9c01a32468f371a8e172c878337fb79757
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule-interface1"></a>ICorDebugModule Interface1
Představuje běžné modul runtime (CLR) jazyk, který je buď spustitelný soubor nebo dynamická knihovna (DLL).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Createbreakpoint – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-createbreakpoint-method.md)|Není implementováno.|  
|[Enableclassloadcallbacks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enableclassloadcallbacks-method.md)|Určuje, zda [icordebugmanagedcallback::loadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [icordebugmanagedcallback::unloadclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) pro tento modul se nazývají zpětných volání.|  
|[Enablejitdebugging – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-enablejitdebugging-method.md)|Určuje, zda kompilátoru za běhu (JIT) uchovává informace o ladění pro metod v rámci tohoto modulu.|  
|[Getassembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md)|Získá obsahující sestavení pro tento modul.|  
|[Getbaseaddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getbaseaddress-method.md)|Získá základní adresu modulu.|  
|[Getclassfromtoken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md)|Získá ICorDebugClass z metadat.|  
|[Geteditandcontinuesnapshot – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-geteditandcontinuesnapshot-method.md)|Zastaralé|  
|[Getfunctionfromrva – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromrva-method.md)|Není implementováno.|  
|[Getfunctionfromtoken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getfunctionfromtoken-method.md)|Získá funkce, která je zadána token metadat.|  
|[Getglobalvariablevalue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getglobalvariablevalue-method.md)|Získá objekt hodnoty pro zadaný globální proměnné.|  
|[Getmetadatainterface – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getmetadatainterface-method.md)|Získá ukazatel rozhraní metadata, která můžete použít k prozkoumání metadata pro modul.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md)|Získá název souboru modulu.|  
|[Getprocess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getprocess-method.md)|Získá obsahující proces pro tento modul.|  
|[Getsize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md)|Získá velikost modulu v bajtech.|  
|[Gettoken – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-gettoken-method.md)|Získá token pro položku tabulky pro tento modul.|  
|[Isdynamic – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isdynamic-method.md)|Určuje, zda je modul dynamické.|  
|[Isinmemory – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-isinmemory-method.md)|Určuje, zda tento modul existuje pouze v paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
