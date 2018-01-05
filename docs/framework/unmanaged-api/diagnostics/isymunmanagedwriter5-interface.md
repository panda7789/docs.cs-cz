---
title: "ISymUnmanagedWriter5 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 15b8526e-4f5d-475c-a1e3-d8b2d145c879
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 701b8de977d49a7d93f393b320bcb9d0d780c7bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter5-interface"></a>ISymUnmanagedWriter5 – rozhraní
Isymunmanagedwriter5 – rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
[object,uuid(DCF7780D-BDE9-45DF-ACFE-21731A32000C),pointer_default(unique)]interface ISymUnmanagedWriter5 : ISymUnmanagedWriter4  
```  
  
## <a name="methods"></a>Metody  
 Toto rozhraní obsahuje následující metody:  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CloseMapTokensToSourceSpans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md)|Zavřete speciální vlastní datové části pro token zdroj span informace o mapování. Po zavření, mohou být přidány žádné další informace o mapování.|  
|[MapTokenToSourceSpan – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-maptokentosourcespan-method.md)|Mapuje token daná metadata na ose zadaná zdrojová span v zadaný zdrojový soubor.<br /><br /> Musí být voláno mezi volání [openmaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md) a [closemaptokenstosourcespans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-closemaptokenstosourcespans-method.md).|  
|[OpenMapTokensToSourceSpans – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-openmaptokenstosourcespans-method.md)|Otevřete část speciální vlastní data pro vydávání informace o tokenu zdroj značky span mapování do. Otevírání v této části, když metoda je již otevřeno, nebo naopak, se o chybu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedWriter4 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
