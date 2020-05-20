---
title: ISymENCUnmanagedMethod – rozhraní
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: 54c8c7f5c3ba6b4afd4ff352a8afb947a92e2d61
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441874"
---
# <a name="isymencunmanagedmethod-interface"></a>ISymENCUnmanagedMethod – rozhraní
Poskytuje informace o funkci upravit a pokračovat.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDocumentsForMethod – metoda](isymencunmanagedmethod-getdocumentsformethod-method.md)|Načte dokumenty, ve kterých tato metoda obsahuje řádky.|  
|[GetDocumentsForMethodCount – metoda](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|Získá počet dokumentů, ve kterých má tato metoda řádky.|  
|[GetFileNameFromOffset – metoda](isymencunmanagedmethod-getfilenamefromoffset-method.md)|Získá název souboru pro řádek přidružený k posunu.|  
|[GetLineFromOffset – metoda](isymencunmanagedmethod-getlinefromoffset-method.md)|Získá informace o řádku přidružené k posunu.|  
|[GetSourceExtentInDocument – metoda](isymencunmanagedmethod-getsourceextentindocument-method.md)|Získá nejmenší počáteční řádek a největšího koncového řádku pro metodu v konkrétním dokumentu.|  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [Rozhraní úložiště symbolů diagnostiky](diagnostics-symbol-store-interfaces.md)
