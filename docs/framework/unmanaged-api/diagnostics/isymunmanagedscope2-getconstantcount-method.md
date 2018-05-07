---
title: ISymUnmanagedScope2::GetConstantCount – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstantCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstantCount
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstantCount method [.NET Framework debugging]
- GetConstantCount method [.NET Framework debugging]
ms.assetid: 1e1f0be6-c4e8-4d6c-98cd-d5fa9f686e87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbe41a3102a61052b2eceae7ccce3b93fd1bef6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedscope2getconstantcount-method"></a>ISymUnmanagedScope2::GetConstantCount – metoda
Získá počet konstanty definované v tomto rozsahu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetConstantCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Ukazatel na `ULONG32` velikostí, která přijme ve znacích vyrovnávací paměti musí obsahovat konstanty.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedScope2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
