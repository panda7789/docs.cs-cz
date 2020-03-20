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
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179001"
---
# <a name="icordebugcodegetcode-method"></a>ICorDebugCode::GetCode – metoda
Vrátí celý kód pro zadanou funkci, který je formátován pro zpětný překlad. Tato metoda byla zastaralá v rozhraní .NET Framework verze 2.0. Použijte [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) místo.  
  
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
 [v] Posun začátku funkce.  
  
 `endOffset`  
 [v] Posun konce funkce.  
  
 `cBufferAlloc`  
 [v] Velikost pole, `buffer` do kterého bude vrácen kód.  
  
 `buffer`  
 [out] Pole, do kterého bude vrácen kód.  
  
 `pcBufferSize`  
 [out] Počet vrácených bajtů.  
  
## <a name="remarks"></a>Poznámky  
 Pokud byl kód funkce rozdělen do více bloků, jsou zřetězeny v pořadí zvyšující se nativní posun. Hranice instrukcí nejsou kontrolovány.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také

- [GetCodeChunks – metoda](icordebugcode2-getcodechunks-method.md)
