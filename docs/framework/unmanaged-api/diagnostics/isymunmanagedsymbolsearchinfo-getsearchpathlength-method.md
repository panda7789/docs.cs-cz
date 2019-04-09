---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 37e9926c8f9677e3b38202c5fb3c43f7b1159edf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170609"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a>ISymUnmanagedSymbolSearchInfo::GetSearchPathLength – metoda
Získá délku cesty hledání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a>Parametry  
 `pcchPath`  
 [out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat délku cesty hledání.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedSymbolSearchInfo – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
