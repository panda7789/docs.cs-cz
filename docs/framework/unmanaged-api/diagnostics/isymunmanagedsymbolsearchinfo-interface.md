---
title: ISymUnmanagedSymbolSearchInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: 30817373-0a21-49c1-a0c4-8e8daeecb8db
topic_type:
- apiref
ms.openlocfilehash: 308c501e17446719067d2dc0580d698c1770bf53
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610662"
---
# <a name="isymunmanagedsymbolsearchinfo-interface"></a>ISymUnmanagedSymbolSearchInfo – rozhraní
Poskytuje metody, které získávají informace o cestě pro hledání. Získejte toto rozhraní voláním `QueryInterface` objektu, který implementuje rozhraní [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetHRESULT – metoda](isymunmanagedsymbolsearchinfo-gethresult-method.md)|Získá HRESULT.|  
|[GetSearchPath – metoda](isymunmanagedsymbolsearchinfo-getsearchpath-method.md)|Získá cestu pro hledání.|  
|[GetSearchPathLength – metoda](isymunmanagedsymbolsearchinfo-getsearchpathlength-method.md)|Získá délku cesty pro hledání.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
