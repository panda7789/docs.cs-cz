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
ms.openlocfilehash: c29656a4787c674886505a3be2508470460dfc10
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136523"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod – rozhraní
Představuje metodu v úložišti symbolů. Toto rozhraní poskytuje přístup pouze na související symbol atributy metody, namísto atributy vztahující se k typu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Získá obor názvů, ve kterém je definována této metody.|  
|[GetOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Vrátí posunutí v rámci této metody, které odpovídá na dané pozici v rámci dokumentu.|  
|[GetParameters – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Získá parametry pro tuto metodu.|  
|[GetRanges – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Danou pozici v dokumentu vrátí pole dvojic počáteční a koncové posunutí, které odpovídají na rozsahy jazyk Microsoft intermediate language (MSIL), která zahrnuje pozici v rámci této metody.|  
|[GetRootScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Získá kořenového oboru lexikální v rámci této metody. Tento rozsah obklopuje celou metodu.|  
|[GetScopeFromOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Získá nejvíce nadřazeného oboru lexikální v rámci této metody, které obklopuje dané posun.|  
|[GetSequencePointCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Získá počet body sekvence v rámci této metody.|  
|[GetSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Získá všechny body sekvence v rámci této metody.|  
|[GetSourceStartEnd – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Získá počáteční a koncové pozice dokumentu pro zdroj této metody.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Vrátí token metadat pro tuto metodu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
