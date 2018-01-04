---
title: "ISymUnmanagedScope2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2
helpviewer_keywords: ISymUnmanagedScope2 interface [.NET Framework debugging]
ms.assetid: 2ed6a387-ba45-483e-9a1e-b0c69f67998b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d2ec846a34b2d3424f7bf8b54f1d4d12d4102e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2-interface"></a>ISymUnmanagedScope2 – rozhraní
Představuje lexikální obor v rámci metody. Toto rozhraní rozšiřuje [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) rozhraní s metody, které získat informace o konstanty definované v rámci oboru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetConstantCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstantcount-method.md)|Získá počet konstanty definované v tomto rozsahu.|  
|[GetConstants – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-getconstants-method.md)|Získá místní konstanty definované v tomto rozsahu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [ISymUnmanagedScope – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
