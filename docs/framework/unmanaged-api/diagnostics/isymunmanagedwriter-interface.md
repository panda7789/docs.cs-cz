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
ms.openlocfilehash: fc19ee25e903046daef376e4297c8feb3d01ad47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427933"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter – rozhraní
Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Zavře zapisovač symbolů bez potvrzení symbolů do úložiště symbolů.|  
|[Close – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbolů.|  
|[CloseMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Zavře aktuální metodu. Po uzavření metody nelze v ní definovat žádné další symboly.|  
|[CloseNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Zavře naposledy otevřený obor názvů.|  
|[CloseScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Zavře aktuální lexikální obor.|  
|[DefineConstant – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Definuje název pro konstantní hodnotu.|  
|[DefineDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Definuje zdrojový dokument.|  
|[DefineField – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Definuje jednu proměnnou, která není v rámci metody.|  
|[DefineGlobalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Definuje jednu globální proměnnou.|  
|[DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|Definuje jednu proměnnou v aktuálním lexikálním oboru.|  
|[DefineParameter – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Definuje jeden parametr v aktuální metodě.|  
|[DefineSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Definuje skupinu bodů sekvence v rámci aktuální metody.|  
|[GetDebugInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Vrátí informace, které jsou nezbytné pro kompilátor pro zápis položky adresáře ladění v hlavičce přenositelného spustitelného souboru (PE).|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Nastaví rozhraní Emit metadat, ke kterému bude tento zapisovač přidružen, a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.|  
|[Initialize2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Nastaví rozhraní Emit metadat, se kterým bude tento zapisovač přidružen, nastaví název výstupního souboru, do kterého budou zapsány symboly ladění, a nastaví konečné umístění souboru databáze programu (PDB).|  
|[OpenMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Otevře metodu, do které jsou vygenerovány informace o symbolech.|  
|[OpenNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Otevře nový obor názvů.|  
|[OpenScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Otevře nový lexikální obor v aktuální metodě.|  
|[RemapToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Upozorní zapisovač symbolů, že token metadat byl přemapován, protože byla vygenerována metadata.|  
|[SetMethodSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Určuje skutečný začátek a konec metody ve zdrojovém souboru.|  
|[SetScopeRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Definuje rozsah posunu pro zadaný lexikální obor.|  
|[SetSymAttribute – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Definuje vlastní atribut založený na jeho názvu.|  
|[SetUserEntryPoint – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Určuje uživatelsky definovanou metodu, která je vstupním bodem pro tento modul.|  
|[UsingNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Určuje, že zadaný plně kvalifikovaný název oboru názvů se používá v aktuálně otevřeném lexikálním oboru.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
