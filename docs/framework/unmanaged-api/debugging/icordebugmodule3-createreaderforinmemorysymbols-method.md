---
title: ICorDebugModule3::CreateReaderForInMemorySymbols – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule3.CreateReaderForInMemorySymbols
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3::CreateReaderForInMemorySymbols
helpviewer_keywords:
- CreateReaderForInMemorySymbols method, ICorDebugModule3 interface [.NET Framework debugging]
- ICorDebugModule3::CreateReaderForInMemorySymbols method [.NET Framework debugging]
ms.assetid: af317171-d66d-4114-89eb-063554c74940
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f553870399a8f2ddb78e01d27a7f7e5bd32d786b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473991"
---
# <a name="icordebugmodule3createreaderforinmemorysymbols-method"></a>ICorDebugModule3::CreateReaderForInMemorySymbols – metoda
Vytvoří čtečku symbolů ladění pro dynamický modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateReaderForInMemorySymbols (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **    ppObj  
```  
  
## <a name="parameters"></a>Parametry  
 riid  
 [in] Identifikátor IID rozhraní COM se vraťte. Obvykle se jedná [isymunmanagedreader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md).  
  
 ppObj  
 [out] Ukazatel na ukazatel na vrácené rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Čtecí modul se úspěšně vytvořil.  
  
 CORDBG_E_MODULE_LOADED_FROM_DISK  
 Modul není v paměti nebo dynamický modul.  
  
 CORDBG_E_SYMBOLS_NOT_AVAILABLE  
 Symboly nebyly poskytnuté aplikací nebo dosud nejsou k dispozici.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nelze vytvořit čtecí modul.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda může také být použité k vytvoření objektu čtečky symbolů pro moduly (nedynamickou) v paměti, ale pouze po symboly jsou k dispozici nejprve (indikován [updatemodulesymbols – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md) zpětného volání).  
  
 Tato metoda vrací novou instanci čtečky pokaždé, když je volána (jako je [CComPtrBase::CoCreateInstance](/cpp/atl/reference/ccomptrbase-class#cocreateinstance)). Proto by měl ladicí program uložte do mezipaměti výsledek a požádat o novou instanci pouze v případě, že mohlo dojít ke změně podkladová data (to znamená, když [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) přijetí zpětné volání).  
  
 Dynamické moduly nemají žádné symboly k dispozici, dokud se načetl první typ (jak je uvedeno ve [loadclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) zpětného volání).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugRemoteTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
