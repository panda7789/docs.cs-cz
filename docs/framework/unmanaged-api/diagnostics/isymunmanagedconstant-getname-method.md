---
title: ISymUnmanagedConstant::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: 2dd70693528904459a34689dbad944c65c971254
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441640"
---
# <a name="isymunmanagedconstantgetname-method"></a>ISymUnmanagedConstant::GetName – metoda
Získá název konstanty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 pro Délka vyrovnávací paměti, `szName` na kterou parametr odkazuje.  
  
 `pcchName`  
 mimo Ukazatel na `ULONG32` , který obdrží velikost vyrovnávací paměti, která je nutná k omezení názvu, včetně ukončení hodnoty null.  
  
 `szName`  
 mimo Vyrovnávací paměť, která ukládá název.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedConstant – rozhraní](isymunmanagedconstant-interface.md)
- [GetSignature – metoda](isymunmanagedconstant-getsignature-method.md)
- [GetValue – metoda](isymunmanagedconstant-getvalue-method.md)
