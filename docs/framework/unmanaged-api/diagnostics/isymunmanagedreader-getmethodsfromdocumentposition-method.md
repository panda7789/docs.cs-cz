---
title: ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodsFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodsFromDocumentPosition
helpviewer_keywords:
- GetMethodsFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodsFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 83605f1e-e4f3-49e6-859b-f13cad68bb54
topic_type:
- apiref
ms.openlocfilehash: 923a92ea256f79a1b0130b61c4fd99460fda96a0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441807"
---
# <a name="isymunmanagedreadergetmethodsfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodsFromDocumentPosition – metoda
Vrátí pole metod, z nichž každý obsahuje zarážku na dané pozici v dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodsFromDocumentPosition (  
    [in]  ISymUnmanagedDocument* document,  
    [in]  ULONG32 line,  
    [in]  ULONG32 column,  
    [in]  ULONG32 cMethod,  
    [out] ULONG32* pcMethod,  
    [out, size_is (cMethod),  
        length_is (*pcMethod)] ISymUnmanagedMethod* pRetVal[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 pro Zadaný dokument.  
  
 `line`  
 pro Řádek zadaného dokumentu.  
  
 `column`  
 pro Sloupec zadaného dokumentu  
  
 `cMethod`  
 pro Velikost pole `pRetVal`.  
  
 `pcMethod`  
 mimo Ukazatel na proměnnou, která přijímá počet prvků vrácených v poli `pRetVal`.  
  
 `pRetVal`  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [ISymUnmanagedMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) , který představuje metodu obsahující zarážku.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
