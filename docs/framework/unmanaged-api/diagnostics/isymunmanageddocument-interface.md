---
title: "ISymUnmanagedDocument – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument
helpviewer_keywords: ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e176679b4fdb4d0a2c5c4fbcbc09403e45f1ad1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocument-interface"></a>ISymUnmanagedDocument – rozhraní
Reprezentuje dokument odkazuje úložiště symbolů. Dokument je definována uniform resource locator (URL) a typ dokumentu identifikátor GUID. Můžete najít v dokumentu bez ohledu na to, jak je uložen pomocí adresy URL a typu GUID dokumentu. Můžete uložit zdrojový dokument do úložiště symbolů a načíst prostřednictvím tohoto rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FindClosestLine – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|Vrátí nejbližší řádek, který je bod pořadí na základě řádku v tomto dokumentu, který může nebo nemusí být bodu sekvence.|  
|[GetCheckSum – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|Získá kontrolního součtu.|  
|[GetCheckSumAlgorithmId – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|Získá identifikátor algoritmu kontrolního součtu, nebo vrátí identifikátor GUID samými nulami, pokud neexistuje žádné kontrolní součet.|  
|[GetDocumentType – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|Získá typ dokumentu tohoto dokumentu.|  
|[GetLanguage – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|Získá identifikátor jazyk tohoto dokumentu.|  
|[GetLanguageVendor – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|Získá jazyk dodavatele tohoto dokumentu.|  
|[GetSourceLength – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|Získá délku, v bajtech embedded zdroje.|  
|[GetSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|Vrátí zadaný rozsah embedded zdroje do dané vyrovnávací paměti.|  
|[GetURL – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|Vrátí adresu URL pro tento dokument.|  
|[HasEmbeddedSource – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|Vrátí `true` jestli má dokument zdroj vložených v symboly pro ladění; jinak vrátí `false`.|  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
