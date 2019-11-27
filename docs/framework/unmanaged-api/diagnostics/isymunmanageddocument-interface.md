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
Představuje dokument, na který odkazuje úložiště symbolů. Dokument je definován pomocí adresy URL (Uniform Resource Locator) a identifikátoru GUID typu dokumentu. Dokument můžete najít bez ohledu na to, jak je uložený, pomocí adresy URL a identifikátoru GUID typu dokumentu. Zdroj dokumentu můžete uložit v úložišti symbolů a načíst ho prostřednictvím tohoto rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindClosestLine – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Vrátí nejbližší řádek, který je sekvenčním bodem, na základě řádku v tomto dokumentu, který může nebo nemusí být bodem sekvence.|  
|[GetCheckSum – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Získá kontrolní součet.|  
|[GetCheckSumAlgorithmId – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Získá identifikátor algoritmu kontrolního součtu nebo vrátí identifikátor GUID všech nul, pokud neexistuje kontrolní součet.|  
|[GetDocumentType – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Získá typ dokumentu tohoto dokumentu.|  
|[GetLanguage – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Získá identifikátor jazyka tohoto dokumentu.|  
|[GetLanguageVendor – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Získá dodavatele jazyka tohoto dokumentu.|  
|[GetSourceLength – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Získá délku vloženého zdroje v bajtech.|  
|[GetSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti.|  
|[GetURL – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Vrátí adresu URL tohoto dokumentu.|  
|[HasEmbeddedSource – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Vrátí `true`, pokud dokument obsahuje zdrojový vložený v symbolech ladění; v opačném případě vrátí `false`.|  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
