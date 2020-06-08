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
ms.openlocfilehash: c0381cf924e44e581c8b275c9750cacba045cf1b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501778"
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
 Tato metoda poskytuje možnost aktualizovat zobrazení symbolů modulu v ladicím programu voláním [ISymUnmanagedReader:: UpdateSymbolStore –](../diagnostics/isymunmanagedreader-updatesymbolstore-method.md) nebo [ISymUnmanagedReader:: ReplaceSymbolStore –](../diagnostics/isymunmanagedreader-replacesymbolstore-method.md).  
  
 Toto zpětné volání může být pro stejný modul provedeno několikrát.  
  
 Ladicí program by se měl pokoušet svázat zarážky na úrovni nevázaného zdroje.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
