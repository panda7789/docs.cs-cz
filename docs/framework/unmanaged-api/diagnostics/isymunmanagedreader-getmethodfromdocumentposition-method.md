---
title: ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodFromDocumentPosition
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodFromDocumentPosition
helpviewer_keywords:
- GetMethodFromDocumentPosition method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodFromDocumentPosition method [.NET Framework debugging]
ms.assetid: 55773dbc-9053-46e3-8a3c-86caa9d91fb4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ed13397748b2668c275b221e38bd75c0dd37f03
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969179"
---
# <a name="isymunmanagedreadergetmethodfromdocumentposition-method"></a>ISymUnmanagedReader::GetMethodFromDocumentPosition – metoda
Vrátí metodu, která obsahuje zarážku na dané pozici v dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodFromDocumentPosition (  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32  line,  
    [in]  ULONG32  column,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `document`  
 [in] Zadaný dokument.  
  
 `line`  
 [in] Řádku zadaný dokument.  
  
 `column`  
 [in] Sloupec zadaný dokument.  
  
 `pRetVal`  
 [out] Ukazatel na adresu [isymunmanagedmethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md) objekt, který představuje metodu obsahující zarážku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
