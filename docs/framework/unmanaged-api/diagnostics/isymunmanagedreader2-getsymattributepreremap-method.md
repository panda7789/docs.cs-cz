---
title: ISymUnmanagedReader2::GetSymAttributePreRemap – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: e6248aba1c41b2815f2806942d419da869ed94b4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614913"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap – metoda
Získá vlastní atribut založený na jeho názvu. Na rozdíl od vlastních atributů metadat jsou tyto atributy uchovávány v úložišti symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `parent`  
 pro Token metadat nadřazeného objektu.  
  
 `name`  
 pro Ukazatel na `WCHAR` , který obsahuje název.  
  
 `cBuffer`  
 pro `ULONG32`Který označuje velikost `buffer` pole.  
  
 `pcBuffer`  
 mimo Ukazatel na `ULONG32` , který přijímá velikost vyrovnávací paměti vyžadované k omezení bajtů atributů.  
  
 `buffer`  
 mimo Ukazatel na vyrovnávací paměť, která přijímá bajty atributů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedReader2 – rozhraní](isymunmanagedreader2-interface.md)
