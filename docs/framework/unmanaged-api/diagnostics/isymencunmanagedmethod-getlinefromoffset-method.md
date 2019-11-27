---
title: ISymENCUnmanagedMethod::GetLineFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 94a571a4bc01b805387aebe5a6e23bad0b735313
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448648"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset – metoda
Získá informace o řádku přidružené k posunu. Pokud parametr posunutí (`dwOffset`) není bodem sekvence, tato metoda získá informace o řádku přidružené k předchozímu posunu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwOffset`  
 pro `ULONG32`, který obsahuje posun.  
  
 `pline`  
 mimo Ukazatel na `ULONG32`, který obdrží řádek.  
  
 `pcolumn`  
 mimo Ukazatel na `ULONG32`, který přijímá sloupec.  
  
 `pendLine`  
 mimo Ukazatel na `ULONG32`, který obdrží koncovou čáru.  
  
 `pendColumn`  
 mimo Ukazatel na `ULONG32`, který obdrží sloupec end.  
  
 `pdwStartOffset`  
 mimo Ukazatel na `ULONG32`, který obdrží přidružený bod sekvence.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymENCUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
