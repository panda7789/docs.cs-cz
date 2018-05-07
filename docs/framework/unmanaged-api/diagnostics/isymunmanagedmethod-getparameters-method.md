---
title: ISymUnmanagedMethod::GetParameters – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fbedb7b1c10dcc2b9b9940db10aae7e4101436b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetparameters-method"></a>ISymUnmanagedMethod::GetParameters – metoda
Získá parametry pro tuto metodu. Parametry jsou vráceny v pořadí, ve kterém jsou definovány v rámci signatury metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cParams`  
 [v] Velikost `params` pole.  
  
 `pcParams`  
 [v] Ukazatel na `ULONG32` která přijme velikost vyrovnávací paměti, kterou musí obsahovat parametry.  
  
 `params`  
 [out] Ukazatel do vyrovnávací paměti, která přijímá parametry.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
