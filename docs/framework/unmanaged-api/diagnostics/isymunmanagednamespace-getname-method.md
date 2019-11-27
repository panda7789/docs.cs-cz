---
title: ISymUnmanagedNamespace::GetName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type:
- apiref
ms.openlocfilehash: 43f32ac85bebc12d0a9253205aae3f1de0dc9e5b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433973"
---
# <a name="isymunmanagednamespacegetname-method"></a>ISymUnmanagedNamespace::GetName – metoda
Získá název tohoto oboru názvů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 pro `ULONG32`, která určuje velikost vyrovnávací paměti `szName`.  
  
 `pcchName`  
 mimo Ukazatel na `ULONG32`, který obdrží velikost vyrovnávací paměti, která je nutná k uložení názvu oboru názvů, včetně ukončení hodnoty null.  
  
 `szName`  
 mimo Ukazatel na vyrovnávací paměť, která obsahuje název oboru názvů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedNamespace – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)
