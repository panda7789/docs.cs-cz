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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9a35f35d7aea34c0ef08c30415fde75fe71e645
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints – metoda
Získá všechny body pořadí v rámci této metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `cPoints`  
 [v] A `ULONG32` která přijme velikost `offsets`, `documents`, `lines`, `columns`, `endLines`, a `endColumns` pole.  
  
 `pcPoints`  
 [out] Ukazatel na `ULONG32` která přijme délka vyrovnávací paměti musí obsahovat body sekvence.  
  
 `offsets`  
 [v] Pole pro uložení zprostředkující Microsoft jazyk MSIL posun od začátku metodu pro body sekvence.  
  
 `documents`  
 [v] Pole, do kterého chcete ukládat dokumenty, ve které se nacházejí body sekvence.  
  
 `lines`  
 [v] Pole pro uložení řádky v dokumentech, na kterých jsou umístěny body sekvence.  
  
 `columns`  
 [v] Pole, do které chcete uložit v dokumentech, na kterých jsou umístěny body pořadí sloupců.  
  
 `endLines`  
 [v] Pole řádků v dokumentech, na kterých je pořadí body end.  
  
 `endColumns`  
 [v] Pole sloupců v dokumentech, na kterých je pořadí body end.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
