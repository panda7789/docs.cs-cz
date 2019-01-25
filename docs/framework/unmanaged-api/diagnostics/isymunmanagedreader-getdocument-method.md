---
title: ISymUnmanagedReader::GetDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ecd11b57d1901c4618ee0d27442753559b85c509
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738102"
---
# <a name="isymunmanagedreadergetdocument-method"></a>ISymUnmanagedReader::GetDocument – metoda
Najde dokument. Jazyk dokumentu, dodavatele a typ jsou volitelné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `url`  
 [in] Adresa URL, která identifikuje dokumentu.  
  
 `language`  
 [in] Jazyk dokumentu. Tento parametr je volitelný.  
  
 `languageVendor`  
 [in] Identita dodavatele jazyka dokumentu. Tento parametr je volitelný.  
  
 `documentType`  
 [in] Typ dokumentu. Tento parametr je volitelný.  
  
 `pRetVal`  
 [out] Ukazatel na vrácené rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
