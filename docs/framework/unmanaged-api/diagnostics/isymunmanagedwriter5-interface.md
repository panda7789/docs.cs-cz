---
title: ISymUnmanagedWriter5 – rozhraní
ms.date: 03/30/2017
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6ed8c6e61c558a4bc9e3f92d559615ac93ecff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962336"
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 – rozhraní
Isymunmanagedwriter5 – rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující dvě metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zavřete speciální vlastní datové části pro token zdroj zahrnovat informace o mapování. Po propojení se zavře, je možné přidat žádné další informace o mapování.|  
|[MapTokenToSourceSpan – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapy token daná metadata do daného zdroje řádku span zadaného zdrojového souboru.<br /><br /> Musí být volána mezi voláními [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otevřete část speciální vlastní data a vygenerovat token zdroj značky span mapování informace do. Otevírání tohoto oddílu při metody je již otevřen nebo naopak, je chybou.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
