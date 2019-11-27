---
title: ISymUnmanagedReader::GetMethodVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: fcaf748413321f684336543e60f735af69894b51
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436008"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a>ISymUnmanagedReader::GetMethodVersion – metoda
Získá verzi metody. Verze metody začíná na 1 a při každém překompilování metody se zvýší. Opětovná kompilace může probíhat beze změn v metodě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a>Parametry  
 `pMethod`  
 pro Metoda, pro kterou se má získat verze  
  
 `version`  
 mimo Ukazatel na proměnnou, která přijímá verzi metody.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
