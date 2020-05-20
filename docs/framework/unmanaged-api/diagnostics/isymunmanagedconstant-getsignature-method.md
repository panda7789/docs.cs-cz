---
title: ISymUnmanagedConstant::GetSignature – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 332d60418c744a9391c7c0afc20248c2239b090c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441617"
---
# <a name="isymunmanagedconstantgetsignature-method"></a>ISymUnmanagedConstant::GetSignature – metoda
Získá signaturu konstanty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cSig`  
 pro Délka vyrovnávací paměti, `pcSig` na kterou parametr odkazuje.  
  
 `pcSig`  
 mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti, která je požadována k podpisu.  
  
 `sig`  
 mimo Vyrovnávací paměť, která ukládá podpis.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedConstant – rozhraní](isymunmanagedconstant-interface.md)
- [GetName – metoda](isymunmanagedconstant-getname-method.md)
- [GetValue – metoda](isymunmanagedconstant-getvalue-method.md)
