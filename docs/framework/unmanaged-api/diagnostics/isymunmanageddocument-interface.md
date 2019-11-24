---
title: ISymUnmanagedDocument – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449105"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument – rozhraní
Represents a document referenced by a symbol store. A document is defined by a uniform resource locator (URL) and a document type GUID. You can locate the document regardless of how it is stored by using the URL and document type GUID. You can store the document source in the symbol store and retrieve it through this interface.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindClosestLine – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.|  
|[GetCheckSum – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Gets the checksum.|  
|[GetCheckSumAlgorithmId – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.|  
|[GetDocumentType – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Gets the document type of this document.|  
|[GetLanguage – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Gets the language identifier of this document.|  
|[GetLanguageVendor – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Gets the language vendor of this document.|  
|[GetSourceLength – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Gets the length, in bytes, of the embedded source.|  
|[GetSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Returns the specified range of the embedded source into the given buffer.|  
|[GetURL – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Returns the URL for this document.|  
|[HasEmbeddedSource – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.|  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
