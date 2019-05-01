---
title: ICorDebugManagedCallback::UpdateModuleSymbols – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UpdateModuleSymbols
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UpdateModuleSymbols
helpviewer_keywords:
- UpdateModuleSymbols method [.NET Framework debugging]
- ICorDebugManagedCallback::UpdateModuleSymbols method [.NET Framework debugging]
ms.assetid: 0863f644-58e8-45a0-b0c3-a28e99b20938
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 581ea4f974bfec3961a32cd7c9985a5e45d2bddd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995065"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols – metoda
Upozorní ladicího programu, že jste změnili symboly pro společný jazykový modul runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující modul, ve kterém jste změnili symboly.  
  
 `pModule`  
 [in] Ukazatel na objekt icordebugmodule –, který představuje modul, ve kterém jste změnili symboly.  
  
 `pSymbolStream`  
 [in] Ukazatel na Win32 COM `IStream` objekt, který obsahuje upravený symboly.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje příležitost k aktualizaci zobrazení ladicího programu modulu symbolů voláním [isymunmanagedreader::updatesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [isymunmanagedreader::replacesymbolstore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 Toto zpětné volání může mít více než jednou stejného modulu.  
  
 Ladicí program se pokuste vytvořit vazbu nevázaného zarážky úroveň zdroje.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
