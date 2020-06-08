---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
ms.openlocfilehash: d9204457b71b670e1c96ed228ad11116bdf41fe6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493575"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 – rozhraní
Rozhraní ISymUnmanagedWriter5  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Description|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans – metoda](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zavřete část speciální vlastní data pro informace o mapování rozsahu z tokenu na zdroj. Po zavření nebudou moci být přidány žádné další informace o mapování.|  
|[MapTokenToSourceSpan – metoda](isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapuje daný token metadat na zadaný rozsah řádku zdroje v zadaném zdrojovém souboru.<br /><br /> Musí být volána mezi voláním [metody openmaptokenstosourcespans –](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [metodou closemaptokenstosourcespans –](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans – metoda](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otevřete zvláštní část s vlastními daty, která vygeneruje informace o mapování rozsahu z tokenu na zdroj do. Otevření této části, pokud je již metoda otevřená, nebo naopak, je chyba.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 – rozhraní](isymunmanagedwriter4-interface.md)
