---
title: ISymUnmanagedConstant::GetValue – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 00be35e9a15349b8bca5f76b948b8477dd240888
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449237"
---
# <a name="isymunmanagedconstantgetvalue-method"></a>ISymUnmanagedConstant::GetValue – metoda
Gets the value of the constant.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pValue`  
 [out] A pointer to a variable that receives the value.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedConstant – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [GetName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [GetSignature – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
