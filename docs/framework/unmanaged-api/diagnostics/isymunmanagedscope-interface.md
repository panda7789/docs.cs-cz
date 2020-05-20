---
title: ISymUnmanagedScope – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope
helpviewer_keywords:
- ISymUnmanagedScope interface [.NET Framework debugging]
ms.assetid: 3db7a220-cfe9-4810-8ca8-a094bb8e0f5b
topic_type:
- apiref
ms.openlocfilehash: 1ee406c97fa4ccb7f87098cba2925568d8ce069f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615342"
---
# <a name="isymunmanagedscope-interface"></a>ISymUnmanagedScope – rozhraní
Představuje lexikální obor v rámci metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetChildren – metoda](isymunmanagedscope-getchildren-method.md)|Získá podřízené objekty tohoto oboru.|  
|[GetEndOffset – metoda](isymunmanagedscope-getendoffset-method.md)|Získá posunutí konce tohoto oboru.|  
|[GetLocalCount – metoda](isymunmanagedscope-getlocalcount-method.md)|Získá počet místních proměnných definovaných v rámci tohoto oboru.|  
|[GetLocals – metoda](isymunmanagedscope-getlocals-method.md)|Získá místní proměnné definované v rámci tohoto oboru.|  
|[GetMethod – metoda](isymunmanagedscope-getmethod-method.md)|Získá metodu, která obsahuje tento obor.|  
|[GetNamespaces – metoda](isymunmanagedscope-getnamespaces-method.md)|Načte obory názvů, které jsou používány v rámci tohoto oboru.|  
|[GetParent – metoda](isymunmanagedscope-getparent-method.md)|Získá nadřazený obor tohoto oboru.|  
|[GetStartOffset – metoda](isymunmanagedscope-getstartoffset-method.md)|Získá posun začátku tohoto oboru.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope2 – rozhraní](isymunmanagedscope2-interface.md)
