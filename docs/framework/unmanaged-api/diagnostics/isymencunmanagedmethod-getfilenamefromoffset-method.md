---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: 857410187edf1c712865626a3327dd4c92cc211f
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441926"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a>ISymENCUnmanagedMethod::GetFileNameFromOffset – metoda
Získá název souboru pro řádek přidružený k posunu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwOffset`  
 pro `ULONG32`, Který obsahuje posun.  
  
 `cchName`  
 pro `ULONG32`Který označuje velikost `szName` vyrovnávací paměti.  
  
 `pcchName`  
 mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k uložení názvů souborů.  
  
 `szName`  
 mimo Vyrovnávací paměť, která obsahuje názvy souborů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymENCUnmanagedMethod – rozhraní](isymencunmanagedmethod-interface.md)
