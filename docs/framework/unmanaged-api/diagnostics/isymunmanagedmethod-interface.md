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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod – rozhraní
Představuje metodu v rámci úložiště symbolů. Toto rozhraní poskytuje přístup k pouze související symbol atributy metody, místo atributy související s typem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Získá obor názvů, ve kterém je tato metoda definována.|  
|[GetOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.|  
|[GetParameters – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Získá parametry pro tuto metodu.|  
|[GetRanges – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Dané pozici v dokumentu vrátí pole počáteční a koncové posunutí párů, které odpovídají na rozsahy Microsoft (MSIL intermediate language) pokrývající pozici v rámci této metody.|  
|[GetRootScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Získá lexikální kořenovém oboru v rámci této metody. Tento obor uzavře celý metoda.|  
|[GetScopeFromOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Získá lexikální nejvíce vymezeném oboru v rámci této metody, která obklopuje daným posunem.|  
|[GetSequencePointCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Získá počet bodů pořadí v rámci této metody.|  
|[GetSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Získá všechny body pořadí v rámci této metody.|  
|[GetSourceStartEnd – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Získá počáteční a koncové pozice dokumentu pro zdroj této metody.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Vrátí metadata token tuto metodu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
