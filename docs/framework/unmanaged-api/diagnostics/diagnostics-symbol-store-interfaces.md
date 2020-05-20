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
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442173"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Rozhraní úložiště symbolů diagnostiky
Toto téma popisuje nespravovaná rozhraní, která umožňují kompilátoru generovat informace o symbolech pro použití v ladicím programu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IBindingDisplay – rozhraní](ibindingdisplay-interface.md)  
 Poskytuje metody, které zobrazují aktuální informace o vazbě spuštěné aplikace.  
  
 [IDebugAutoAttach – rozhraní](idebugautoattach-interface.md)  
 Definuje rozhraní pro automatické připojování ladicího programu spouštěného serverem.  
  
 [INotifyConnection2 – rozhraní](inotifyconnection2-interface.md)  
 Deklaruje metody pro registraci a zrušení registrace zdroje oznámení o připojení.  
  
 [INotifySink2 – rozhraní](inotifysink2-interface.md)  
 Deklaruje metody pro oznámení jímky.  
  
 [INotifySource2 – rozhraní](inotifysource2-interface.md)  
 Deklaruje metodu pro nastavení filtrů oznámení.  
  
 [ISymENCUnmanagedMethod – rozhraní](isymencunmanagedmethod-interface.md)  
 Poskytuje informace o funkci upravit a pokračovat.  
  
 [ISymUnmanagedAsyncMethod – rozhraní](isymunmanagedasyncmethod-interface.md)  
 Toto rozhraní je doplňkem pro čtení [rozhraní ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter – rozhraní](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Umožňuje definici nepovinné informace o asynchronní metodě na symbol metody. Musí používat s otevřenou metodou (to znamená mezi voláním [metody OpenMethod –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)a [metodou CloseMethod –](isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder – rozhraní](isymunmanagedbinder-interface.md)  
 Představuje pořadač symbolů pro nespravovaný kód.  
  
 [ISymUnmanagedBinder2 – rozhraní](isymunmanagedbinder2-interface.md)  
 Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje `ISymUnmanagedBinder` rozhraní.  
  
 [ISymUnmanagedBinder3 – rozhraní](isymunmanagedbinder3-interface.md)  
 Představuje pořadač symbolů pro nespravovaný kód a rozšiřuje `ISymUnmanagedBinder` rozhraní.  
  
 [ISymUnmanagedConstant – rozhraní](isymunmanagedconstant-interface.md)  
 Poskytuje přístup k nespravovaným konstantám.  
  
 [ISymUnmanagedDispose – rozhraní](isymunmanageddispose-interface.md)  
 Likvidace nespravovaných prostředků.  
  
 [ISymUnmanagedDocument – rozhraní](isymunmanageddocument-interface.md)  
 Představuje dokument, na který odkazuje úložiště symbolů.  
  
 [ISymUnmanagedDocumentWriter – rozhraní](isymunmanageddocumentwriter-interface.md)  
 Poskytuje metody pro zápis do dokumentu, na který odkazuje úložiště symbolů.  
  
 [ISymUnmanagedENCUpdate – rozhraní](isymunmanagedencupdate-interface.md)  
 Poskytuje metody pro funkci upravit a pokračovat.  
  
 [ISymUnmanagedMethod – rozhraní](isymunmanagedmethod-interface.md)  
 Představuje metodu v úložišti symbolů.  
  
 [ISymUnmanagedNamespace – rozhraní](isymunmanagednamespace-interface.md)  
 Představuje obor názvů.  
  
 [ISymUnmanagedReader – rozhraní](isymunmanagedreader-interface.md)  
 Představuje čtečku symbolů, která poskytuje přístup k dokumentům, metodám a proměnným v rámci úložiště symbolů.  
  
 [ISymUnmanagedReader2 – rozhraní](isymunmanagedreader2-interface.md)  
 Získá metodu čtečky symbolů pro token metody a číslo verze pro úpravy a kopírování.  
  
 [ISymUnmanagedReaderSymbolSearchInfo – rozhraní](isymunmanagedreadersymbolsearchinfo-interface.md)  
 Poskytuje metody, které získávají informace o hledání symbolů.  
  
 [ISymUnmanagedScope – rozhraní](isymunmanagedscope-interface.md)  
 Představuje lexikální obor v rámci metody.  
  
 [ISymUnmanagedScope2 – rozhraní](isymunmanagedscope2-interface.md)  
 Představuje lexikální obor v rámci metody a rozšiřuje `ISymUnmanagedScope` rozhraní o metody, které získávají informace o konstantách definovaných v rámci oboru.  
  
 [ISymUnmanagedSourceServerModule – rozhraní](isymunmanagedsourceservermodule-interface.md)  
 Poskytuje data zdrojového serveru pro modul.  
  
 [ISymUnmanagedSymbolSearchInfo – rozhraní](isymunmanagedsymbolsearchinfo-interface.md)  
 Poskytuje metody, které získávají informace o cestě pro hledání.  
  
 [ISymUnmanagedVariable – rozhraní](isymunmanagedvariable-interface.md)  
 Představuje proměnnou, jako je například parametr, místní proměnná nebo pole.  
  
 [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)  
 Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.  
  
 [ISymUnmanagedWriter2 – rozhraní](isymunmanagedwriter2-interface.md)  
 Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných. Rozšiřuje `ISymUnmanagedWriter` rozhraní.  
  
 [ISymUnmanagedWriter3 – rozhraní](isymunmanagedwriter3-interface.md)  
 Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných. Rozšiřuje `ISymUnmanagedWriter` rozhraní.  
  
 [ISymUnmanagedWriter4 – rozhraní](isymunmanagedwriter4-interface.md)  
 Rozhraní Isymunmanagedwriter4 –  
  
 [ISymUnmanagedWriter5 – rozhraní](isymunmanagedwriter5-interface.md)  
 Rozhraní ISymUnmanagedWriter5  
  
## <a name="related-sections"></a>Související oddíly  
 [Výčty úložiště symbolů diagnostiky](diagnostics-symbol-store-enumerations.md)  
  
 [Struktury úložiště symbolů diagnostiky](diagnostics-symbol-store-structures.md)  
  
 [Ladění](../debugging/index.md)
