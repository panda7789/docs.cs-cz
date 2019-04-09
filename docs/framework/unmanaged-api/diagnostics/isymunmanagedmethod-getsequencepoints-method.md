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
ms.openlocfilehash: f6b1e253fb7bf1a97f44e1eb05676fc356af9837
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123705"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a>ISymUnmanagedMethod::GetSequencePoints – metoda
Získá všechny body sekvence v rámci této metody.  
  
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
  
## <a name="parameters"></a>Parametry  
 `cPoints`  
 [in] A `ULONG32` , která obdrží velikost `offsets`, `documents`, `lines`, `columns`, `endLines`, a `endColumns` pole.  
  
 `pcPoints`  
 [out] Ukazatel `ULONG32` , která obdrží délka vyrovnávací paměti musí obsahovat body sekvence.  
  
 `offsets`  
 [in] Pole pro uložení Microsoft intermediate language (MSIL) posun od začátku metody pro body sekvence.  
  
 `documents`  
 [in] Pole ve kterých se mají ukládat dokumenty, ve kterých jsou umístěny body sekvence.  
  
 `lines`  
 [in] Pole pro uložení řádky v dokumentech, na kterých jsou umístěny body sekvence.  
  
 `columns`  
 [in] Pole pro uložení sloupce v dokumentech, na kterých jsou umístěny body sekvence.  
  
 `endLines`  
 [in] Pole řádků v dokumentech, na které odkazuje sekvence end.  
  
 `endColumns`  
 [in] Pole sloupců v dokumentech, na které odkazuje sekvence end.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
