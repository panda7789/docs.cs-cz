---
title: ISymUnmanagedReader::GetSymbolStoreFileName – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 147b33a3f49f9163daea776779ca26f62561a84e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170375"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a>ISymUnmanagedReader::GetSymbolStoreFileName – metoda
Poskytuje název souboru na disku úložiště symbolů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cchName`  
 [in] Velikost `szName` vyrovnávací paměti.  
  
 `pcchName`  
 [out] Ukazatel na proměnnou, která přijímá délka názvu vrátil v `szName`, včetně ukončení hodnotu null.  
  
 `szName`  
 [out] Ukazatel na proměnnou, která přijímá název souboru v úložišti symbolů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
