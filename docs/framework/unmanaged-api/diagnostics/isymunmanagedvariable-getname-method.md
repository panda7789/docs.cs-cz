---
title: ISymUnmanagedVariable::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5aa6f01f161ce7c497cc103493e3bf4506fa3394
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57475018"
---
# <a name="isymunmanagedvariablegetname-method"></a>ISymUnmanagedVariable::GetName – metoda
Získá název této proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Délka vyrovnávací paměti, která `pcchName` parametr odkazuje na.  
  
 `pcchName`  
 [out] Ukazatel `ULONG32` , která obdrží velikost ve znacích, vyrovnávací paměti musí obsahovat název, včetně ukončení hodnotu null.  
  
 `szName`  
 [out] Vyrovnávací paměť, která ukládá název.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:
- [ISymUnmanagedVariable – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
