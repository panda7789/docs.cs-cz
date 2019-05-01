---
title: ISymUnmanagedWriter – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ac95cd5b79a2e1762fa9adf29d4d7926ab4ab7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986060"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter – rozhraní
Reprezentuje zapisovač symbolů a poskytuje metody, které definují dokumenty, body sekvence, lexikální obory a proměnné.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Zavře zapisovač symbol bez potvrzení symbolů do úložiště symbolů.|  
|[Close – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbol.|  
|[CloseMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Zavře aktuální metoda. Po zavření metodu žádné další symboly lze definovat v něm.|  
|[CloseNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Zavře otevřít naposledy oboru názvů.|  
|[CloseScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Zavře aktuální lexikálním rozsahu.|  
|[DefineConstant – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Definuje název pro konstantní hodnotu.|  
|[DefineDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Definuje zdrojový dokument.|  
|[DefineField – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Definuje jednu proměnnou, která není v rámci metody.|  
|[DefineGlobalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Definuje jeden globální proměnné.|  
|[DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|V aktuálním oboru lexikální definuje jednu proměnnou.|  
|[DefineParameter – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Definuje jeden parametr v aktuální metodě.|  
|[DefineSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Definuje skupinu pořadí bodů v aktuální metodě.|  
|[GetDebugInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Vrací informace nezbytné pro kompilátor zapsat záznam adresáře ladění přenosný spustitelný soubor hlavičky souboru (PE).|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Nastaví rozhraní vysílače metadat, díky které bude tento zapisovač přidružené a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.|  
|[Initialize2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Nastaví rozhraní vysílače metadat, pomocí kterého budou přidruženy tento zapisovač, nastaví název výstupního souboru, ke kterému se zapíše symboly ladění a nastaví konečné umístění souboru databáze (PDB) programu.|  
|[OpenMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Otevře se metoda, do které symbol je vygenerován informace.|  
|[OpenNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Otevře se nový obor názvů.|  
|[OpenScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Otevře se nový lexikální rozsah v aktuální metodě.|  
|[RemapToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Upozorní zapisovač symbol, že má jako metadata generovalo přemapování token metadat.|  
|[SetMethodSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Určuje hodnotu true začátku a konce metody v rámci zdrojového souboru.|  
|[SetScopeRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Definuje rozsah pro zadaný obor lexikální posunu.|  
|[SetSymAttribute – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Definuje vlastní atribut na základě jeho názvu.|  
|[SetUserEntryPoint – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Určuje metodu definovaný uživatelem, která je vstupním bodem pro tento modul.|  
|[UsingNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Určuje, že daný plně kvalifikovaný obor názvů je používán v rámci oboru lexikální aktuálně otevřené.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
