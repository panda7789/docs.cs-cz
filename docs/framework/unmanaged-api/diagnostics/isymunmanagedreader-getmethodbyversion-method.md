---
title: ISymUnmanagedReader::GetMethodByVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4bc763d908156f3bbf8998c13073820686903f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986372"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a>ISymUnmanagedReader::GetMethodByVersion – metoda
Získá metodu čtečky symbolů daný token metody a číslo verze upravit a kopírovat. Čísla verzí začínají znakem 1 a jsou zvětšeny pokaždé, když metoda se změnilo v důsledku operace upravit a kopírovat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `token`  
 [in] Token metody.  
  
 `version`  
 [in] Metoda verze.  
  
 `pRetVal`  
 [out] Ukazatel na vrácené rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
