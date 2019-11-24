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
ms.openlocfilehash: 401dfbea0da309db24f3052f462daa66e8bbef4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449265"
---
# <a name="isymunmanagedconstantgetsignature-method"></a>ISymUnmanagedConstant::GetSignature – metoda
Gets the signature of the constant.  
  
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
 [in] The length of the buffer that the `pcSig` parameter points to.  
  
 `pcSig`  
 [out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.  
  
 `sig`  
 [out] The buffer that stores the signature.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedConstant – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [GetName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [GetValue – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
