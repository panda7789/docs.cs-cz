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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615563"
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument – rozhraní
Představuje dokument, na který odkazuje úložiště symbolů. Dokument je definován pomocí adresy URL (Uniform Resource Locator) a identifikátoru GUID typu dokumentu. Dokument můžete najít bez ohledu na to, jak je uložený, pomocí adresy URL a identifikátoru GUID typu dokumentu. Zdroj dokumentu můžete uložit v úložišti symbolů a načíst ho prostřednictvím tohoto rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindClosestLine – metoda](isymunmanageddocument-findclosestline-method.md)|Vrátí nejbližší řádek, který je sekvenčním bodem, na základě řádku v tomto dokumentu, který může nebo nemusí být bodem sekvence.|  
|[GetCheckSum – metoda](isymunmanageddocument-getchecksum-method.md)|Získá kontrolní součet.|  
|[GetCheckSumAlgorithmId – metoda](isymunmanageddocument-getchecksumalgorithmid-method.md)|Získá identifikátor algoritmu kontrolního součtu nebo vrátí identifikátor GUID všech nul, pokud neexistuje kontrolní součet.|  
|[GetDocumentType – metoda](isymunmanageddocument-getdocumenttype-method.md)|Získá typ dokumentu tohoto dokumentu.|  
|[GetLanguage – metoda](isymunmanageddocument-getlanguage-method.md)|Získá identifikátor jazyka tohoto dokumentu.|  
|[GetLanguageVendor – metoda](isymunmanageddocument-getlanguagevendor-method.md)|Získá dodavatele jazyka tohoto dokumentu.|  
|[GetSourceLength – metoda](isymunmanageddocument-getsourcelength-method.md)|Získá délku vloženého zdroje v bajtech.|  
|[GetSourceRange – metoda](isymunmanageddocument-getsourcerange-method.md)|Vrátí zadaný rozsah vloženého zdroje do dané vyrovnávací paměti.|  
|[GetURL – metoda](isymunmanageddocument-geturl-method.md)|Vrátí adresu URL tohoto dokumentu.|  
|[HasEmbeddedSource – metoda](isymunmanageddocument-hasembeddedsource-method.md)|Vrátí, `true` zda má dokument ve symbolech ladění zdroj vložený. v opačném případě vrátí `false` .|  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
