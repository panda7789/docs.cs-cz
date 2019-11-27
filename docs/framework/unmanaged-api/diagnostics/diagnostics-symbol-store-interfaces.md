---
title: Rozhraní úložiště symbolů diagnostiky
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448522"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Rozhraní úložiště symbolů diagnostiky
Toto téma popisuje nespravovaná rozhraní, která umožňují kompilátoru generovat informace o symbolech pro použití v ladicím programu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IBindingDisplay – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Poskytuje metody, které zobrazují aktuální informace o vazbě spuštěné aplikace.  
  
 [IDebugAutoAttach – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Definuje rozhraní pro automatické připojování ladicího programu spouštěného serverem.  
  
 [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Deklaruje metody pro registraci a zrušení registrace zdroje oznámení o připojení.  
  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Deklaruje metody pro oznámení jímky.  
  
 [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Deklaruje metodu pro nastavení filtrů oznámení.  
  
 [ISymENCUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Poskytuje informace o funkci upravit a pokračovat.  
  
 [ISymUnmanagedAsyncMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Umožňuje definici nepovinné informace o asynchronní metodě na symbol metody. Musí používat s otevřenou metodou (to znamená mezi voláním [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [metodou CloseMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Představuje pořadač symbolů pro nespravovaný kód.  
  
 [ISymUnmanagedBinder2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní `ISymUnmanagedBinder`.  
  
 [ISymUnmanagedBinder3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje rozhraní `ISymUnmanagedBinder`.  
  
 [ISymUnmanagedConstant – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Poskytuje přístup k nespravovaným konstantám.  
  
 [ISymUnmanagedDispose – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Likvidace nespravovaných prostředků.  
  
 [ISymUnmanagedDocument – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Představuje dokument, na který odkazuje úložiště symbolů.  
  
 [ISymUnmanagedDocumentWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Poskytuje metody pro zápis do dokumentu, na který odkazuje úložiště symbolů.  
  
 [ISymUnmanagedENCUpdate – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Poskytuje metody pro funkci upravit a pokračovat.  
  
 [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Představuje metodu v úložišti symbolů.  
  
 [ISymUnmanagedNamespace – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Představuje obor názvů.  
  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.  
  
 [ISymUnmanagedReader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Získá metodu čtečky symbolů pro token metody a číslo verze pro úpravy a kopírování.  
  
 [ISymUnmanagedReaderSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Poskytuje metody, které získávají informace o hledání symbolů.  
  
 [ISymUnmanagedScope – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Představuje lexikální obor v rámci metody.  
  
 [ISymUnmanagedScope2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Představuje lexikální obor v rámci metody a rozšiřuje rozhraní `ISymUnmanagedScope` s metodami, které získávají informace o konstantách definovaných v rámci oboru.  
  
 [ISymUnmanagedSourceServerModule – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Poskytuje data zdrojového serveru pro modul.  
  
 [ISymUnmanagedSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Poskytuje metody, které získávají informace o cestě pro hledání.  
  
 [ISymUnmanagedVariable – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.  
  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.  
  
 [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných. Rozšiřuje rozhraní `ISymUnmanagedWriter`.  
  
 [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných. Rozšiřuje rozhraní `ISymUnmanagedWriter`.  
  
 [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Rozhraní Isymunmanagedwriter4 –  
  
 [ISymUnmanagedWriter5 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Rozhraní ISymUnmanagedWriter5  
  
## <a name="related-sections"></a>Související oddíly  
 [Výčty pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Struktury pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
