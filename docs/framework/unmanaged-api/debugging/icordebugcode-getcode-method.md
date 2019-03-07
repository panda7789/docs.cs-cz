---
title: ICorDebugCode::GetCode – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b69970d50652da203ecf1ae6fe8d604ccee06cf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483572"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode – metoda
Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0. Použití [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `startOffset`  
 [in] Posun zahájení funkce.  
  
 `endOffset`  
 [in] Posun od konce funkce.  
  
 `cBufferAlloc`  
 [in] Velikost `buffer` pole, do které bude vrácen kód.  
  
 `buffer`  
 [out] Pole, do kterého bude vrácen kód.  
  
 `pcBufferSize`  
 [out] Počet bajtů vrácených.  
  
## <a name="remarks"></a>Poznámky  
 Pokud funkce kód byl rozdělen do více bloků dat, jsou spojeny v pořadí podle zvýšení nativní posun. Instrukce hranice nekontrolují.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:
- [GetCodeChunks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)

