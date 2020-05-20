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
ms.openlocfilehash: d9a7b18e90a3038c1ffb634ccc7315143875c809
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441913"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a>ISymENCUnmanagedMethod::GetLineFromOffset – metoda
Získá informace o řádku přidružené k posunu. Pokud parametr offset ( `dwOffset` ) není bodem sekvence, tato metoda získá informace o řádku přidružené k předchozímu posunu.  
  
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
 pro `ULONG32`, Který obsahuje posun.  
  
 `pline`  
 mimo Ukazatel `ULONG32` , který získá řádek.  
  
 `pcolumn`  
 mimo Ukazatel na `ULONG32` , který přijímá sloupec.  
  
 `pendLine`  
 mimo Ukazatel na `ULONG32` , který získá koncovou čáru.  
  
 `pendColumn`  
 mimo Ukazatel na `ULONG32` , který získá sloupec end.  
  
 `pdwStartOffset`  
 mimo Ukazatel na `ULONG32` , který obdrží přidružený bod sekvence.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymENCUnmanagedMethod – rozhraní](isymencunmanagedmethod-interface.md)
