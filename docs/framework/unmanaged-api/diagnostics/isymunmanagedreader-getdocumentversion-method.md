---
title: ISymUnmanagedReader::GetDocumentVersion – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocumentVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocumentVersion
helpviewer_keywords:
- GetDocumentVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetDocumentVersion method [.NET Framework debugging]
ms.assetid: a51f1f64-e084-44c5-830c-2222da5a6bbf
topic_type:
- apiref
ms.openlocfilehash: 3bc578be680951a1d41c92fb2169c860882b2e31
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448306"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion – metoda
Načte zadanou verzi zadaného dokumentu. Verze dokumentu začíná 1 a při každém aktualizování dokumentu pomocí metody [UpdateSymbolStore –](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) se zvýší. Pokud je parametr `pbCurrent` `true`, jedná se o nejnovější verzi dokumentu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDocumentVersion (  
    [in]  ISymUnmanagedDocument *pDoc,  
    [out] int* version,  
    [out] BOOL* pbCurrent);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDoc`  
 pro Zadaný dokument.  
  
 `version`  
 mimo Ukazatel na proměnnou, která přijímá verzi zadaného dokumentu.  
  
 `pbCurrent`  
 mimo Ukazatel na proměnnou, která přijímá `true`, pokud se jedná o nejnovější verzi dokumentu, nebo `false`, pokud se nejedná o nejnovější verzi.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedReader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
