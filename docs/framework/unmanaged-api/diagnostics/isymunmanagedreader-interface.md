---
title: "ISymUnmanagedReader – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader
helpviewer_keywords: ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 56e0012ae1412c0fb5b434d3b4c0221831296c60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader – rozhraní
Představuje čtečku symbol, který poskytuje přístup k dokumentům, metod a proměnné v rámci úložiště symbolů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Vyhledá dokumentu.|  
|[Getdocuments – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Vrátí pole všech dokumentů, které jsou definované v úložišti symbol.|  
|[Getdocumentversion – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Získá určenou verzi zadaný dokument.|  
|[GetGlobalVariables – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Vrátí všechny globální proměnné.|  
|[Getmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Získá metody čtečky symbol, zadaný token metoda.|  
|[Getmethodbyversion – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Získá metody čtečky symbol, zadaný token metoda a čísla verze úpravy a kopie.|  
|[Getmethodfromdocumentposition – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Vrátí metodu, která obsahuje bod přerušení na dané pozici v dokumentu.|  
|[Getmethodsfromdocumentposition – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Vrátí pole metod, z nichž každý obsahuje zarážek na dané pozici v dokumentu.|  
|[Getmethodversion – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Získá verzi metoda.|  
|[Getnamespaces – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Získá oborů názvů definovaných v globálním oboru v rámci úložiště tento symbol.|  
|[Getsymattribute – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Získá vlastní atribut na základě jeho názvu.|  
|[Getsymbolstorefilename – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Obsahuje název souboru na disku úložiště symbolů.|  
|[Getuserentrypoint – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Vrátí metodu, která byla zadána jako vstupní bod uživatele modulu, pokud existuje.|  
|[Getvariables – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Vrátí proměnnou jiné než místní, daného jeho nadřazený a název.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Inicializuje čtečky symbol s rozhraním program pro import metadat, které bude tato čtečky spojený s, spolu s názvem souboru modulu.|  
|[Replacesymbolstore – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Nahradí existující úložiště symbolů s úložištěm symbol delta.|  
|[Updatesymbolstore – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Aktualizuje existující úložiště symbolů s úložištěm symbol delta.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [Isymunmanagedreader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
