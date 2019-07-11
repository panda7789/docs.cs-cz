---
title: ISymUnmanagedReader::GetGlobalVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de246c8b9c4387ea782b77f16edfbe792bb4427
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777011"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a>ISymUnmanagedReader::GetGlobalVariables – metoda
Vrátí všechny globální proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cVars`  
 [in] Délka vyrovnávací paměti na které odkazuje `pcVars`.  
  
 `pcVars`  
 [out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat proměnné.  
  
 `pVars`  
 [out] Vyrovnávací paměť obsahující proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
