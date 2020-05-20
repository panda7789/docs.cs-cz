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
ms.openlocfilehash: c2cc541b2a78f16d5ca6b19405794faa825a9d72
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615030"
---
# <a name="isymunmanagedreadergetdocumentversion-method"></a>ISymUnmanagedReader::GetDocumentVersion – metoda
Načte zadanou verzi zadaného dokumentu. Verze dokumentu začíná 1 a při každém aktualizování dokumentu pomocí metody [UpdateSymbolStore –](isymunmanagedreader-updatesymbolstore-method.md) se zvýší. Pokud `pbCurrent` je parametr `true` , jedná se o nejnovější verzi dokumentu.  
  
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
 mimo Ukazatel na proměnnou, která obdrží, `true` Pokud se jedná o nejnovější verzi dokumentu, nebo pokud se `false` nejedná o nejnovější verzi.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedReader – rozhraní](isymunmanagedreader-interface.md)
