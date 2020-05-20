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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615121"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod – rozhraní
Představuje metodu v úložišti symbolů. Toto rozhraní poskytuje přístup pouze k atributům, které se vztahují k symbolům metody, namísto atributů souvisejících s typem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetNamespace – metoda](isymunmanagedmethod-getnamespace-method.md)|Získá obor názvů, ve kterém je tato metoda definována.|  
|[GetOffset – metoda](isymunmanagedmethod-getoffset-method.md)|Vrátí posun v rámci této metody, který odpovídá dané pozici v rámci dokumentu.|  
|[GetParameters – metoda](isymunmanagedmethod-getparameters-method.md)|Získá parametry pro tuto metodu.|  
|[GetRanges – metoda](isymunmanagedmethod-getranges-method.md)|Vzhledem k pozici v dokumentu vrátí pole párů počátečního a koncového posunu, které odpovídají rozsahům v rámci této metody, které odpovídají rozsahům jazyka MSIL (Microsoft Intermediate Language), které umístění pokrývá.|  
|[GetRootScope – metoda](isymunmanagedmethod-getrootscope-method.md)|Získá kořenový lexikální rozsah v rámci této metody. Tento obor uzavírá celou metodu.|  
|[GetScopeFromOffset – metoda](isymunmanagedmethod-getscopefromoffset-method.md)|Získá nejvíce ohraničující lexikální obor v rámci této metody, která uzavře daný posun.|  
|[GetSequencePointCount – metoda](isymunmanagedmethod-getsequencepointcount-method.md)|Získá počet bodů sekvence v rámci této metody.|  
|[GetSequencePoints – metoda](isymunmanagedmethod-getsequencepoints-method.md)|Načte všechny body sekvence v rámci této metody.|  
|[GetSourceStartEnd – metoda](isymunmanagedmethod-getsourcestartend-method.md)|Získá pozice počátečního a koncového dokumentu pro zdroj této metody.|  
|[GetToken – metoda](isymunmanagedmethod-gettoken-method.md)|Vrátí token metadat pro tuto metodu.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
