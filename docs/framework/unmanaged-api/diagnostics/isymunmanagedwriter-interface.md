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
ms.openlocfilehash: 8f0bbd26bde562df5482d167c9d2775e01426f55
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610051"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter – rozhraní
Představuje zapisovač symbolů a poskytuje metody pro definování dokumentů, sekvenčních bodů, lexikálních oborů a proměnných.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](isymunmanagedwriter-abort-method.md)|Zavře zapisovač symbolů bez potvrzení symbolů do úložiště symbolů.|  
|[Close – metoda](isymunmanagedwriter-close-method.md)|Po potvrzení symbolů do úložiště symbolů zavře zapisovač symbolů.|  
|[CloseMethod – metoda](isymunmanagedwriter-closemethod-method.md)|Zavře aktuální metodu. Po uzavření metody nelze v ní definovat žádné další symboly.|  
|[CloseNamespace – metoda](isymunmanagedwriter-closenamespace-method.md)|Zavře naposledy otevřený obor názvů.|  
|[CloseScope – metoda](isymunmanagedwriter-closescope-method.md)|Zavře aktuální lexikální obor.|  
|[DefineConstant – metoda](isymunmanagedwriter-defineconstant-method.md)|Definuje název pro konstantní hodnotu.|  
|[DefineDocument – metoda](isymunmanagedwriter-definedocument-method.md)|Definuje zdrojový dokument.|  
|[DefineField – metoda](isymunmanagedwriter-definefield-method.md)|Definuje jednu proměnnou, která není v rámci metody.|  
|[DefineGlobalVariable – metoda](isymunmanagedwriter-defineglobalvariable-method.md)|Definuje jednu globální proměnnou.|  
|[DefineLocalVariable – metoda](isymunmanagedwriter-definelocalvariable-method.md)|Definuje jednu proměnnou v aktuálním lexikálním oboru.|  
|[DefineParameter – metoda](isymunmanagedwriter-defineparameter-method.md)|Definuje jeden parametr v aktuální metodě.|  
|[DefineSequencePoints – metoda](isymunmanagedwriter-definesequencepoints-method.md)|Definuje skupinu bodů sekvence v rámci aktuální metody.|  
|[GetDebugInfo – metoda](isymunmanagedwriter-getdebuginfo-method.md)|Vrátí informace, které jsou nezbytné pro kompilátor pro zápis položky adresáře ladění v hlavičce přenositelného spustitelného souboru (PE).|  
|[Initialize – metoda](isymunmanagedwriter-initialize-method.md)|Nastaví rozhraní Emit metadat, ke kterému bude tento zapisovač přidružen, a nastaví název výstupního souboru, do kterého budou zapsány symboly ladění.|  
|[Initialize2 – metoda](isymunmanagedwriter-initialize2-method.md)|Nastaví rozhraní Emit metadat, se kterým bude tento zapisovač přidružen, nastaví název výstupního souboru, do kterého budou zapsány symboly ladění, a nastaví konečné umístění souboru databáze programu (PDB).|  
|[OpenMethod – metoda](isymunmanagedwriter-openmethod-method.md)|Otevře metodu, do které jsou vygenerovány informace o symbolech.|  
|[OpenNamespace – metoda](isymunmanagedwriter-opennamespace-method.md)|Otevře nový obor názvů.|  
|[OpenScope – metoda](isymunmanagedwriter-openscope-method.md)|Otevře nový lexikální obor v aktuální metodě.|  
|[RemapToken – metoda](isymunmanagedwriter-remaptoken-method.md)|Upozorní zapisovač symbolů, že token metadat byl přemapován, protože byla vygenerována metadata.|  
|[SetMethodSourceRange – metoda](isymunmanagedwriter-setmethodsourcerange-method.md)|Určuje skutečný začátek a konec metody ve zdrojovém souboru.|  
|[SetScopeRange – metoda](isymunmanagedwriter-setscoperange-method.md)|Definuje rozsah posunu pro zadaný lexikální obor.|  
|[SetSymAttribute – metoda](isymunmanagedwriter-setsymattribute-method.md)|Definuje vlastní atribut založený na jeho názvu.|  
|[SetUserEntryPoint – metoda](isymunmanagedwriter-setuserentrypoint-method.md)|Určuje uživatelsky definovanou metodu, která je vstupním bodem pro tento modul.|  
|[UsingNamespace – metoda](isymunmanagedwriter-usingnamespace-method.md)|Určuje, že zadaný plně kvalifikovaný název oboru názvů se používá v aktuálně otevřeném lexikálním oboru.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 – rozhraní](isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 – rozhraní](isymunmanagedwriter3-interface.md)
