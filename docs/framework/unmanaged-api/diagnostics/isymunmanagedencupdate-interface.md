---
title: ISymUnmanagedENCUpdate – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: f3305a7bb003fc50f772f1100f8a17d385e4d5fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449002"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate – rozhraní
Provides functions for the Edit and Continue feature.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetLocalVariableCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariablecount-method.md)|Gets the number of local variables.|  
|[GetLocalVariables – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-getlocalvariables-method.md)|Gets the local variables.|  
|[InitializeForEnc – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.|  
|[UpdateMethodLines – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatemethodlines-method.md)|Allows updating the line information for a method that has not been recompiled, but whose lines have moved independently. A delta for each statement is allowed.|  
|[UpdateSymbolStore2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md)|Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided that the line information meets the requirements. The correct line information can be determined with the old PDB line information and one delta for all lines in the function.|  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
