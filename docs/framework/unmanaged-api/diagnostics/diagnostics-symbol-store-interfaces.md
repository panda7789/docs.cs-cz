---
title: "Rozhraní úložiště symbolů diagnostiky"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a9550bf1e3e5500356584b1bdd53f5d3061e190
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a>Rozhraní úložiště symbolů diagnostiky
Toto téma popisuje nespravovaná rozhraní, které umožňují kompilátoru ke generování informací o symbolu za účelem použití ladicí program.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IBindingDisplay – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Poskytuje metody, které zobrazují aktuální informace o vazbě o běžící aplikaci.  
  
 [IDebugAutoAttach – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Definuje rozhraní pro připojení serveru vyvolá ladicí program automaticky.  
  
 [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Deklaruje metody pro registraci a zrušení registrace oznámení zdroj připojení.  
  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Deklaruje metody pro podřízený oznámení.  
  
 [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Deklaruje metodu pro nastavení oznámení filtry.  
  
 [ISymENCUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Obsahuje informace o funkci upravit a pokračovat.  
  
 [ISymUnmanagedAsyncMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Toto rozhraní je doplňkovým čtení na [isymunmanagedasyncmethodpropertieswriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Umožňuje definici volitelné asynchronní metoda informace za metoda symbol. Musíte použít s otevřenou metodu (to znamená, mezi volání [openmethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [closemethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Představuje vazač symbol pro nespravovaného kódu.  
  
 [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Představuje vazač symbol pro nespravovaného kódu a rozšiřuje `ISymUnmanagedBinder` rozhraní.  
  
 [ISymUnmanagedBinder3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Představuje vazač symbol pro nespravovaného kódu a rozšiřuje `ISymUnmanagedBinder` rozhraní.  
  
 [ISymUnmanagedConstant – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Poskytuje přístup k nespravované konstanty.  
  
 [ISymUnmanagedDispose – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Uvolní nespravované prostředky.  
  
 [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Reprezentuje dokument odkazuje úložiště symbolů.  
  
 [ISymUnmanagedDocumentWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Poskytuje metody pro zápis do dokumentu odkazuje úložiště symbolů.  
  
 [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Poskytuje metody pro funkci upravit a pokračovat.  
  
 [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Představuje metodu v rámci úložiště symbolů.  
  
 [ISymUnmanagedNamespace – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Představuje obor názvů.  
  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Představuje čtečku symbol, který poskytuje přístup k dokumentům, metod a proměnné v rámci úložiště symbolů.  
  
 [ISymUnmanagedReader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Získá metody čtečky symbol daného token metoda a číslo verze úpravy a kopie.  
  
 [ISymUnmanagedReaderSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Poskytuje metody, které získání informací o symbolu vyhledávání.  
  
 [ISymUnmanagedScope – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Představuje lexikální obor v rámci metody.  
  
 [ISymUnmanagedScope2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Představuje lexikální obor v rámci metody a rozšiřuje `ISymUnmanagedScope` rozhraní s metody, které získat informace o konstanty definované v rámci oboru...  
  
 [ISymUnmanagedSourceServerModule – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Pro modul poskytuje data zdrojového serveru.  
  
 [ISymUnmanagedSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Poskytuje metody, které získat informace o cestě pro vyhledávání.  
  
 [ISymUnmanagedVariable – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Představuje proměnnou, třeba parametr, místní proměnné nebo pole.  
  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.  
  
 [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné. Rozšiřuje `ISymUnmanagedWriter` rozhraní.  
  
 [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné. Rozšiřuje `ISymUnmanagedWriter` rozhraní.  
  
 [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Isymunmanagedwriter4 – rozhraní.  
  
 [ISymUnmanagedWriter5 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Isymunmanagedwriter5 – rozhraní.  
  
## <a name="related-sections"></a>Související oddíly  
 [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
