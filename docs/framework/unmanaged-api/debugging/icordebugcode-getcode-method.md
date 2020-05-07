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
ms.openlocfilehash: 59a497d203d241bbc6e0f884007d4a401c112073
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893656"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode – metoda
Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugCode2:: getcodechunks –](icordebugcode2-getcodechunks-method.md) .  
  
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
 pro Velikost `buffer` pole, do něhož bude vrácen kód.  
  
 `buffer`  
 mimo Pole, do kterého bude vrácen kód.  
  
 `pcBufferSize`  
 mimo Počet vrácených bajtů  
  
## <a name="remarks"></a>Poznámky  
 Pokud byl kód funkce rozdělen do více bloků dat, jsou zřetězeny v pořadí, ve kterém se zvyšuje nativní posun. Nekontrolují se hranice instrukcí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Viz také

- [GetCodeChunks – metoda](icordebugcode2-getcodechunks-method.md)
