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
ms.openlocfilehash: 7ae978f5d2c9f7e90f4549c15a3935b441eabf04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434005"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader – rozhraní
Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Najde dokument.|  
|[GetDocuments – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Vrátí pole všech dokumentů definovaných v úložišti symbolů.|  
|[GetDocumentVersion – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Načte zadanou verzi zadaného dokumentu.|  
|[GetGlobalVariables – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Vrátí všechny globální proměnné.|  
|[GetMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Získá metodu čtečky symbolů s ohledem na token metody.|  
|[GetMethodByVersion – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Získá metodu čtečky symbolů s ohledem na token metody a číslo verze pro úpravy a kopírování.|  
|[GetMethodFromDocumentPosition – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.|  
|[GetMethodsFromDocumentPosition – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Vrátí pole metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.|  
|[GetMethodVersion – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Získá verzi metody.|  
|[GetNamespaces – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Načte obory názvů definované v globálním oboru v rámci tohoto úložiště symbolů.|  
|[GetSymAttribute – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Získá vlastní atribut založený na jeho názvu.|  
|[GetSymbolStoreFileName – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Poskytuje název souboru na disku pro úložiště symbolů.|  
|[GetUserEntryPoint – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Vrátí metodu, která byla zadána jako vstupní bod uživatele pro modul, pokud existuje.|  
|[GetVariables – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Vrátí nemístní proměnnou, která má zadaný nadřazený prvek a název.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Inicializuje čtečku symbolů pomocí rozhraní pro import metadat, ke kterému bude tento čtenář přidružen, společně s názvem souboru modulu.|  
|[ReplaceSymbolStore – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Nahradí existující úložiště symbolů rozdílovým úložištěm symbolů.|  
|[UpdateSymbolStore – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje existující úložiště symbolů pomocí rozdílového úložiště symbolů.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
