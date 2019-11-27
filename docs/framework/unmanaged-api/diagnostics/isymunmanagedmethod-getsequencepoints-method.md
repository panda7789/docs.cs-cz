---
title: ISymUnmanagedMethod::GetSequencePoints – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 75d477af7395a9b7d3328b2a5787f810733f3749
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448873"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints – metoda
Načte všechny body sekvence v rámci této metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cPoints`  
 pro `ULONG32`, která přijímá velikost `offsets`, `documents`, `lines`, `columns`, `endLines`a `endColumns` polí.  
  
 `pcPoints`  
 mimo Ukazatel na `ULONG32`, který přijímá délku vyrovnávací paměti vyžadované k umístění bodů sekvence.  
  
 `offsets`  
 pro Pole, do kterého se má uložit posun jazyka MSIL (Microsoft Intermediate Language) od začátku metody pro body sekvence.  
  
 `documents`  
 pro Pole, do kterého se mají ukládat dokumenty, ve kterých jsou umístěny body sekvence.  
  
 `lines`  
 pro Pole, do kterého se mají ukládat řádky v dokumentech, ve kterých jsou umístěny body sekvence.  
  
 `columns`  
 pro Pole, do kterého se mají ukládat sloupce v dokumentech, ve kterých jsou umístěny body sekvence.  
  
 `endLines`  
 pro Pole řádků v dokumentech, na kterých končí body sekvence  
  
 `endColumns`  
 pro Pole sloupců v dokumentech, na kterých končí body sekvence  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
