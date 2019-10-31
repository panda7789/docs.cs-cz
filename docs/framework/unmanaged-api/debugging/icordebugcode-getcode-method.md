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
ms.openlocfilehash: db24228de7e8c98fd97f890b1e408515172299b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125674"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode – metoda
Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugCode2:: getcodechunks –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Posun začátku funkce  
  
 `endOffset`  
 pro Posun konce funkce  
  
 `cBufferAlloc`  
 pro Velikost pole `buffer`, do něhož bude vrácen kód.  
  
 `buffer`  
 mimo Pole, do kterého bude vrácen kód.  
  
 `pcBufferSize`  
 mimo Počet vrácených bajtů  
  
## <a name="remarks"></a>Poznámky  
 Pokud byl kód funkce rozdělen do více bloků dat, jsou zřetězeny v pořadí, ve kterém se zvyšuje nativní posun. Nekontrolují se hranice instrukcí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Viz také:

- [GetCodeChunks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)
