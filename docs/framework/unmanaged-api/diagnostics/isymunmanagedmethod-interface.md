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
Představuje metodu v úložišti symbolů. Toto rozhraní poskytuje přístup pouze k atributům, které se vztahují k symbolům metody, namísto atributů souvisejících s typem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetNamespace – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|Získá obor názvů, ve kterém je tato metoda definována.|  
|[GetOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|Vrátí posun v rámci této metody, který odpovídá dané pozici v rámci dokumentu.|  
|[GetParameters – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|Získá parametry pro tuto metodu.|  
|[GetRanges – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|Vzhledem k pozici v dokumentu vrátí pole párů počátečního a koncového posunu, které odpovídají rozsahům v rámci této metody, které odpovídají rozsahům jazyka MSIL (Microsoft Intermediate Language), které umístění pokrývá.|  
|[GetRootScope – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|Získá kořenový lexikální rozsah v rámci této metody. Tento obor uzavírá celou metodu.|  
|[GetScopeFromOffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|Získá nejvíce ohraničující lexikální obor v rámci této metody, která uzavře daný posun.|  
|[GetSequencePointCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|Získá počet bodů sekvence v rámci této metody.|  
|[GetSequencePoints – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|Načte všechny body sekvence v rámci této metody.|  
|[GetSourceStartEnd – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|Získá pozice počátečního a koncového dokumentu pro zdroj této metody.|  
|[GetToken – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|Vrátí token metadat pro tuto metodu.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
