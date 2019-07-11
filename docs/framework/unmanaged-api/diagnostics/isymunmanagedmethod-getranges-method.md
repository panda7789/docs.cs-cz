---
title: ISymUnmanagedMethod::GetRanges – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRanges
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRanges
helpviewer_keywords:
- ISymUnmanagedMethod::GetRanges method [.NET Framework debugging]
- GetRanges method [.NET Framework debugging]
ms.assetid: a85283d8-379c-417a-9736-ddeeef9bcf50
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef5a98d510eee8942a2cad0525b6902e3e4eaa52
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769384"
---
# <a name="isymunmanagedmethodgetranges-method"></a>ISymUnmanagedMethod::GetRanges – metoda
Danou pozici v dokumentu vrátí pole dvojic počáteční a koncové posunutí, které odpovídají na rozsahy jazyk Microsoft intermediate language (MSIL), která zahrnuje pozici v rámci této metody. Pole je pole celých čísel a má formát [spuštění, end, zahájení, ukončení]. Počet dvojic rozsah je délka pole, děleno 2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRanges(  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32                line,  
    [in]  ULONG32                column,  
    [in]  ULONG32                cRanges,  
    [out] ULONG32                *pcRanges,  
    [out, size_is(cRanges),  
        length_is(*pcRanges)] ULONG32 ranges[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 [in] Dokument, pro kterou je požadována posun.  
  
 `line`  
 [in] Dokument řádek odpovídající oblasti.  
  
 `column`  
 [in] Sloupec dokumentu odpovídající oblasti.  
  
 `cRanges`  
 [in] Velikost `ranges` pole.  
  
 `pcRanges`  
 [out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat rozsahy.  
  
 `ranges`  
 [out] Ukazatel do vyrovnávací paměti, která přijímá rozsahů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
