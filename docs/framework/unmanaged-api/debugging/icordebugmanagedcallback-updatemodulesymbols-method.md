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
ms.openlocfilehash: 9ee6f43c94b8ff2e765d2a0dde0697c4c895a94f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212370"
---
# <a name="icordebugmanagedcallbackupdatemodulesymbols-method"></a>ICorDebugManagedCallback::UpdateModuleSymbols – metoda
Oznamuje ladicímu programu, že se změnily symboly pro modul CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT UpdateModuleSymbols (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule,  
    [in] IStream            *pSymbolStream  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující modul, ve kterém byly symboly změněny.  
  
 `pModule`  
 pro Ukazatel na objekt ICorDebugModule, který představuje modul, ve kterém byly symboly změněny.  
  
 `pSymbolStream`  
 pro Ukazatel na objekt modelu COM Win32 `IStream` , který obsahuje upravené symboly.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda poskytuje možnost aktualizovat zobrazení symbolů modulu v ladicím programu voláním [ISymUnmanagedReader:: UpdateSymbolStore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [ISymUnmanagedReader:: ReplaceSymbolStore –](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 Toto zpětné volání může být pro stejný modul provedeno několikrát.  
  
 Ladicí program by se měl pokoušet svázat zarážky na úrovni nevázaného zdroje.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
