---
title: ISymUnmanagedReaderSymbolSearchInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo
helpviewer_keywords:
- ISymUnmanagedReaderSymbolSearchInfo interface [.NET Framework debugging]
ms.assetid: fde7e21d-1169-4bed-a34d-792e69652bf9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a872774b1c4510c8d0325c59ae7678c867c1aff
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59216805"
---
# <a name="isymunmanagedreadersymbolsearchinfo-interface"></a>ISymUnmanagedReaderSymbolSearchInfo – rozhraní
Poskytuje metody, které získávají informace hledání symbolu. Získat po zavolání tohoto rozhraní `QueryInterface` na objekt, který implementuje [isymunmanagedreader –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) rozhraní.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetSymbolSearchInfo – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfo-method.md)|Získá informace hledání symbolu.|  
|[GetSymbolSearchInfoCount – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-getsymbolsearchinfocount-method.md)|Získá počet informace hledání symbolu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní úložiště symbolů diagnostiky](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
