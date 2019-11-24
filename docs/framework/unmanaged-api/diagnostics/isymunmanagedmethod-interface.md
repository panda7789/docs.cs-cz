---
title: ISymUnmanagedMethod – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448781"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod – rozhraní
Represents a method within the symbol store. This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Gets the namespace within which this method is defined.|  
|[GetOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Returns the offset within this method that corresponds to a given position within a document.|  
|[GetParameters – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Gets the parameters for this method.|  
|[GetRanges – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.|  
|[GetRootScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Gets the root lexical scope within this method. This scope encloses the entire method.|  
|[GetScopeFromOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Gets the most enclosing lexical scope within this method that encloses the given offset.|  
|[GetSequencePointCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Gets the count of sequence points within this method.|  
|[GetSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Gets all the sequence points within this method.|  
|[GetSourceStartEnd – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Gets the start and end document positions for the source of this method.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Returns the metadata token for this method.|  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
