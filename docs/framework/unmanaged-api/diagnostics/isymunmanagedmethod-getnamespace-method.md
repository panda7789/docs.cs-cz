---
title: ISymUnmanagedMethod::GetNamespace – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: b8bbedb4c60a2df6070373f2b6a104fff094869a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448963"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a>ISymUnmanagedMethod::GetNamespace – metoda
Získá obor názvů, ve kterém je tato metoda definována.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRetVal`  
 mimo Ukazatel, který je nastaven na vrácené rozhraní [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
