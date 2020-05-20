---
title: ISymUnmanagedReader – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: b372021fcda39d9973d96a9c39e93e38617887a6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615459"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader – rozhraní
Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDocument – metoda](isymunmanagedreader-getdocument-method.md)|Najde dokument.|  
|[GetDocuments – metoda](isymunmanagedreader-getdocuments-method.md)|Vrátí pole všech dokumentů definovaných v úložišti symbolů.|  
|[GetDocumentVersion – metoda](isymunmanagedreader-getdocumentversion-method.md)|Načte zadanou verzi zadaného dokumentu.|  
|[GetGlobalVariables – metoda](isymunmanagedreader-getglobalvariables-method.md)|Vrátí všechny globální proměnné.|  
|[GetMethod – metoda](isymunmanagedreader-getmethod-method.md)|Získá metodu čtečky symbolů s ohledem na token metody.|  
|[GetMethodByVersion – metoda](isymunmanagedreader-getmethodbyversion-method.md)|Získá metodu čtečky symbolů s ohledem na token metody a číslo verze pro úpravy a kopírování.|  
|[GetMethodFromDocumentPosition – metoda](isymunmanagedreader-getmethodfromdocumentposition-method.md)|Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.|  
|[GetMethodsFromDocumentPosition – metoda](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Vrátí pole metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.|  
|[GetMethodVersion – metoda](isymunmanagedreader-getmethodversion-method.md)|Získá verzi metody.|  
|[GetNamespaces – metoda](isymunmanagedreader-getnamespaces-method.md)|Načte obory názvů definované v globálním oboru v rámci tohoto úložiště symbolů.|  
|[GetSymAttribute – metoda](isymunmanagedreader-getsymattribute-method.md)|Získá vlastní atribut založený na jeho názvu.|  
|[GetSymbolStoreFileName – metoda](isymunmanagedreader-getsymbolstorefilename-method.md)|Poskytuje název souboru na disku pro úložiště symbolů.|  
|[GetUserEntryPoint – metoda](isymunmanagedreader-getuserentrypoint-method.md)|Vrátí metodu, která byla zadána jako vstupní bod uživatele pro modul, pokud existuje.|  
|[GetVariables – metoda](isymunmanagedreader-getvariables-method.md)|Vrátí nemístní proměnnou, která má zadaný nadřazený prvek a název.|  
|[Initialize – metoda](isymunmanagedreader-initialize-method.md)|Inicializuje čtečku symbolů pomocí rozhraní pro import metadat, ke kterému bude tento čtenář přidružen, společně s názvem souboru modulu.|  
|[ReplaceSymbolStore – metoda](isymunmanagedreader-replacesymbolstore-method.md)|Nahradí existující úložiště symbolů rozdílovým úložištěm symbolů.|  
|[UpdateSymbolStore – metoda](isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 – rozhraní](isymunmanagedreader2-interface.md)
