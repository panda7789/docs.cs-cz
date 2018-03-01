---
title: "ISymUnmanagedReader::GetDocument – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 00ded0e7e88cacbcedb66e1cef27e4f5eaaf4d29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a>ISymUnmanagedReader::GetDocument – metoda
Vyhledá dokumentu. Jazyk dokumentu, dodavatele a typ jsou volitelné.  
  
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
 [v] Adresa URL, která identifikuje dokumentu.  
  
 `language`  
 [v] Jazyk dokumentu. Tento parametr je volitelný.  
  
 `languageVendor`  
 [v] Identita dodavatele pro jazyk dokumentu. Tento parametr je volitelný.  
  
 `documentType`  
 [v] Typ dokumentu. Tento parametr je volitelný.  
  
 `pRetVal`  
 [out] Ukazatel rozhraní vrácená.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
