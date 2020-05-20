---
title: ISymUnmanagedWriter::DefineDocument – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
ms.openlocfilehash: fdcfb0c4f9c21eb516f4196d0c8f682669468219
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615225"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a>ISymUnmanagedWriter::DefineDocument – metoda
Definuje zdrojový dokument. Pro známé jazyky, dodavatele a typy dokumentů jsou k dispozici identifikátory GUID.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `url`  
 pro Ukazatel na `WCHAR` , který definuje adresu URL (Uniform Resource Locator), která identifikuje dokument.  
  
 `language`  
 pro Ukazatel na identifikátor GUID, který definuje jazyk dokumentu.  
  
 `languageVendor`  
 pro Ukazatel na identifikátor GUID, který definuje identitu dodavatele pro jazyk dokumentu.  
  
 `documentType`  
 pro Ukazatel na identifikátor GUID definující typ dokumentu.  
  
 `pRetVal`  
 mimo Ukazatel na vrácené rozhraní [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) .  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také

- [ISymUnmanagedWriter – rozhraní](isymunmanagedwriter-interface.md)
