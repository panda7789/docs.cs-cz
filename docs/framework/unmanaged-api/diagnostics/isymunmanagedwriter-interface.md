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
ms.openlocfilehash: 86aa8d3d23d82d51cfe4e6ce6b15b554704ad41c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435469"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter – rozhraní
Reprezentuje zapisovač symbol a poskytuje metody k definování dokumenty, body sekvence, lexikální oborů a proměnné.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Abort – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Zavře zapisovače symbol bez potvrzení symboly pro úložiště symbolů.|  
|[Close – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Zavře zapisovače symbol po potvrzení symboly pro úložiště symbolů.|  
|[CloseMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|Zavře aktuální metoda. Jakmile je uzavřený metodu, může být definováno žádné další symboly v něm.|  
|[CloseNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Zavře naposledy Otevřít obor názvů.|  
|[CloseScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|Zavře aktuální lexikální obor.|  
|[DefineConstant – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Definuje název pro konstantní hodnotu.|  
|[DefineDocument – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|Definuje zdrojový dokument.|  
|[DefineField – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Definuje samostatná proměnná, která není v rámci metody.|  
|[DefineGlobalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Definuje jeden globální proměnné.|  
|[DefineLocalVariable – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|V aktuálním oboru lexikální definuje jednu proměnnou.|  
|[DefineParameter – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Definuje jeden parametr v aktuální metoda.|  
|[DefineSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|Definuje skupinu bodů pořadí v rámci aktuální metoda.|  
|[GetDebugInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Vrací informace potřebné pro kompilátor zapsat záznam adresáře ladění přenosné hlavičky spustitelného souboru (PE).|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený a název výstupního souboru, ke kterému se zapíšou symboly pro ladění.|  
|[Initialize2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Nastaví rozhraní vysílače metadata, pomocí kterého bude tento zapisovač spojený, nastaví název výstupního souboru, ke které se zapíše symboly pro ladění a nastaví konečné umístění souboru databáze (PDB).|  
|[OpenMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Otevře se metoda, do které symbol informace jsou vydávány.|  
|[OpenNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|Otevře se nový obor názvů.|  
|[OpenScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|Otevře nové lexikální obor v aktuální metoda.|  
|[RemapToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Upozorní zapisovače symbol, že token metadat jako metadata byla vygenerované složek.|  
|[SetMethodSourceRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Určuje hodnotu true počáteční a koncová metody v rámci zdrojového souboru.|  
|[SetScopeRange – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|Definuje rozsah pro zadaný obor lexikální posunu.|  
|[SetSymAttribute – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Definuje vlastní atribut na základě jeho názvu.|  
|[SetUserEntryPoint – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Určuje metodu definovaný uživatelem, která je vstupní bod pro tento modul.|  
|[UsingNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Určuje, že zadaný obor názvů plně kvalifikovaný název je používán v rámci oboru lexikální aktuálně otevřené.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
