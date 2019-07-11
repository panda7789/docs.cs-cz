---
title: ISymUnmanagedWriter::DefineDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9a36e094689696b746fcf7f10c282a1b0d9c570
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777835"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument – metoda
Definuje zdrojový dokument. Identifikátory GUID jsou k dispozici pro známé jazyky, dodavatele a typů dokumentů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `url`  
 [in] Ukazatel `WCHAR` , který určuje adresu uniform resource locator (URL), který identifikuje dokumentu.  
  
 `language`  
 [in] Ukazatel na identifikátor GUID, který definuje jazyk dokumentu.  
  
 `languageVendor`  
 [in] Ukazatel na identifikátor GUID, který definuje totožnost dodavatele jazyka dokumentu.  
  
 `documentType`  
 [in] Ukazatel na identifikátor GUID, který definuje typ dokumentu.  
  
 `pRetVal`  
 [out] Ukazatel na vrácenou [isymunmanagedwriter –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
