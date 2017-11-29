---
title: "ICorDebugModule3::CreateReaderForInMemorySymbols – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3.CreateReaderForInMemorySymbols
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fbab155e783d3b5e40da466fef56633317c67042
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols – metoda
Vytvoří symbol čtečku ladění pro dynamické modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
#### <a name="parameters"></a>Parametry  
 riid  
 [v] Identifikátory IID rozhraní COM vrátit. Obvykle se jedná [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Ukazatel na ukazatel na vrácený rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Čtečka se úspěšně vytvořil.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Modul není modul v paměti nebo dynamické.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Symboly aplikací, nebyla zadána nebo ještě nejsou k dispozici.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nelze vytvořit program pro čtení.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda může být také použít k vytvoření objektu čtečky symbol pro moduly (bez dynamické) v paměti, ale pouze po symboly jsou k dispozici nejprve (indikován [updatemodulesymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) zpětného volání).  
  
 Tato metoda vrátí novou instanci čtečky pokaždé, když je volána (jako je [CComPtrBase::CoCreateInstance](http://msdn.microsoft.com/library/c0965041-6cb6-40c5-b272-2b99f02668a6)). Proto by měl ladicího programu mezipaměti výsledek a jenom v případě, že mohlo dojít ke změně v základních datech požádat o novou instanci (to znamená, když [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) přijetí zpětného volání).  
  
 Dynamických modulech nemají žádné symboly, které jsou k dispozici, dokud se načetl první typ (jak [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) zpětného volání).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRemoteTarget – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [ICorDebug – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
