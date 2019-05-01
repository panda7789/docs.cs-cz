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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 543a8015e944333942b619060059273577902a74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986333"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a>ISymUnmanagedReader2::GetSymAttributePreRemap – metoda
Získá vlastní atribut na základě jeho názvu. Na rozdíl od vlastních atributů metadat tyto atributy jsou uložené v úložišti symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Token metadat nadřazeného prvku.  
  
 `name`  
 [in] Ukazatel `WCHAR` , který obsahuje název.  
  
 `cBuffer`  
 [in] A `ULONG32` , který označuje velikost `buffer` pole.  
  
 `pcBuffer`  
 [out] Ukazatel `ULONG32` , která obdrží velikost vyrovnávací paměti musí obsahovat atribut bajtů.  
  
 `buffer`  
 [out] Ukazatel do vyrovnávací paměti, který přijímá atribut bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
