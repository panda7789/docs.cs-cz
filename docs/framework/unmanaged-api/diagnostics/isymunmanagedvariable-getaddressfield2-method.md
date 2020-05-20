---
title: ISymUnmanagedVariable::GetAddressField2 – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
ms.openlocfilehash: 6256d052780b1c610e61267be2517954d722a42d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610597"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a>ISymUnmanagedVariable::GetAddressField2 – metoda
Získá druhé pole adresy pro tuto proměnnou. Jeho význam závisí na typu adresy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel na `ULONG32` , který obdrží druhé pole adresy.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedVariable – rozhraní](isymunmanagedvariable-interface.md)
- [GetAddressField1 – metoda](isymunmanagedvariable-getaddressfield1-method.md)
- [GetAddressField3 – metoda](isymunmanagedvariable-getaddressfield3-method.md)
- [GetAddressKind – metoda](isymunmanagedvariable-getaddresskind-method.md)
