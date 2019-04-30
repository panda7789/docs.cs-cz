---
title: ISymUnmanagedMethod::GetToken – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ec6e25452a40ae67570badde8a883878d103f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939565"
---
# <a name="isymunmanagedmethodgettoken-method"></a>ISymUnmanagedMethod::GetToken – metoda
Vrátí token metadat pro tuto metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a>Parametry  
 `pToken`  
 [out] Ukazatel `mdMethodDef` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat metadata.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
