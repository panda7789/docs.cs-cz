---
title: ISymUnmanagedNamespace::GetVariables – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
ms.openlocfilehash: 98ed5556020b93fb1f31d1dde84690fc33092627
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448370"
---
# <a name="isymunmanagednamespacegetvariables-method"></a>ISymUnmanagedNamespace::GetVariables – metoda
Vrátí všechny proměnné definované v globálním oboru v rámci tohoto oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cVars`  
 pro `ULONG32`, která určuje velikost `pVars` pole.  
  
 `pcVars`  
 mimo Ukazatel na `ULONG32`, který přijímá velikost vyrovnávací paměti vyžadované k omezení oboru názvů.  
  
 `pVars`  
 mimo Ukazatel na vyrovnávací paměť, která obsahuje obory názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedNamespace – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
