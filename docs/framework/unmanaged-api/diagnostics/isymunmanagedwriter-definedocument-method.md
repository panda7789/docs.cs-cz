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
ms.openlocfilehash: 02b270677131d0960db67b0ac8db38cba2b5e2df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428054"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument – metoda
Defines a source document. GUIDs are provided for known languages, vendors, and document types.  
  
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
 [in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.  
  
 `language`  
 [in] A pointer to a GUID that defines the document language.  
  
 `languageVendor`  
 [in] A pointer to a GUID that defines the identity of the vendor for the document language.  
  
 `documentType`  
 [in] A pointer to a GUID that defines the type of the document.  
  
 `pRetVal`  
 [out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
