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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1043a7efe70798fbbc52ce6d1d0e16510e7c0503
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499142"
---
# <a name="isymunmanagedconstantgetvalue-method"></a>ISymUnmanagedConstant::GetValue – metoda
Získá hodnotu konstanty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pValue`  
 [out] Ukazatel na proměnnou, která přijímá hodnotu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedConstant – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [GetName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [GetSignature – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
