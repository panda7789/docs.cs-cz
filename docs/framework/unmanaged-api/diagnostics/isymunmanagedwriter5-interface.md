---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: bdc630c3c94c7d03b736efa0a95665f10aac7c6e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609427"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 – rozhraní
Rozhraní ISymUnmanagedWriter5  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans – metoda](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj. Po zavření nebudou moci být přidány žádné další informace o mapování.|  
|[MapTokenToSourceSpan – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.<br /><br /> Musí být volána mezi voláním [metody openmaptokenstosourcespans –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans – metoda](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do. Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 – rozhraní](isymunmanagedwriter4-interface.md)
