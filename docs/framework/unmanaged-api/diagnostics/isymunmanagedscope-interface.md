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
ms.openlocfilehash: 8da4da38d23ed65a0fdc44a0f919ee8cad2fe18e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446262"
---
# <a name="isymunmanagedscope-interface"></a>ISymUnmanagedScope – rozhraní
Represents a lexical scope within a method.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetChildren – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getchildren-method.md)|Gets the children of this scope.|  
|[GetEndOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getendoffset-method.md)|Gets the end offset for this scope.|  
|[GetLocalCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocalcount-method.md)|Gets a count of the local variables defined within this scope.|  
|[GetLocals – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getlocals-method.md)|Gets the local variables defined within this scope.|  
|[GetMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getmethod-method.md)|Gets the method that contains this scope.|  
|[GetNamespaces – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getnamespaces-method.md)|Gets the namespaces that are being used within this scope.|  
|[GetParent – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)|Gets the parent scope of this scope.|  
|[GetStartOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getstartoffset-method.md)|Gets the start offset for this scope.|  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedScope2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)
