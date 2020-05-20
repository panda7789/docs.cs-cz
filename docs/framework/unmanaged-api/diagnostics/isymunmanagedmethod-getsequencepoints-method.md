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
ms.openlocfilehash: 451cfecde7e14fad9d3fed3367112e1fb59796e5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615141"
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
 pro A `ULONG32` který přijímá velikost `offsets` `documents` polí,, `lines` , `columns` , `endLines` a `endColumns` .  
  
 `pcPoints`  
 mimo Ukazatel na `ULONG32` , který přijímá délku vyrovnávací paměti vyžadované k umístění bodů sekvence.  
  
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
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedMethod – rozhraní](isymunmanagedmethod-interface.md)
