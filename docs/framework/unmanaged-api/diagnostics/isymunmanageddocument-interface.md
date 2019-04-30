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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 33213aced635549dd439cf679d89367a71baa7c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939773"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument – rozhraní
Reprezentuje dokument odkazuje úložiště symbolů. Dokument je definována uniform resource locator (URL) a typu dokumentu identifikátor GUID. Můžete vyhledat dokumentu bez ohledu na to, jak se uloží s použitím adresy URL a identifikátor GUID typu dokumentu. Můžete ukládat zdrojový dokument v úložišti symbolů a načíst pomocí tohoto rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindClosestLine – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Vrátí nejbližší řádek, který je bodu sekvence. Zadaný řádek v tomto dokumentu, který může nebo nemusí být bodu sekvence.|  
|[GetCheckSum – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Získá kontrolní součet.|  
|[GetCheckSumAlgorithmId – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.|  
|[GetDocumentType – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Získá typ dokumentu tohoto dokumentu.|  
|[GetLanguage – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Získá identifikátor jazyka tohoto dokumentu.|  
|[GetLanguageVendor – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Získá jazyk dodavatele tohoto dokumentu.|  
|[GetSourceLength – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Získá délku v bajtech vloženého zdroje.|  
|[GetSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Vrátí zadaný rozsah vloženého zdroje do daného vyrovnávací paměti.|  
|[GetURL – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Vrátí adresu URL pro tento dokument.|  
|[HasEmbeddedSource – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Vrátí `true` Pokud dokument má zdroj součástí symboly ladění; v opačném případě vrátí `false`.|  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
