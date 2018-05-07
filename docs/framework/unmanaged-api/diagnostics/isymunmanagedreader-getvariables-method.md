---
title: ISymUnmanagedReader::GetVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74df7ee71fc541c35bc393f637ad1d7b9f7aa2a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedreadergetvariables-method"></a>ISymUnmanagedReader::GetVariables – metoda
Vrátí proměnnou jiné než místní, na základě jeho nadřazený a název.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `parent`  
 [v] Nadřazené proměnnou.  
  
 `cVars`  
 [v] Velikost `pVars` pole.  
  
 `pcVars`  
 [out] Ukazatel na proměnnou, která přijímá počet proměnných, vrátí se v `pVars`.  
  
 `pVars`  
 [out] Ukazatel na proměnnou, která přijímá proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
