---
title: ISymUnmanagedDocumentWriter::SetCheckSum – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: dbf876a514ce106c566a168f688eb3a22d3a1ea2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449044"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a>ISymUnmanagedDocumentWriter::SetCheckSum – metoda
Nastaví informace kontrolního součtu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `algorithmId`  
 pro Identifikátor GUID, který představuje identifikátor algoritmu.  
  
 `checkSumSize`  
 pro `ULONG32`, která určuje velikost vyrovnávací paměti `checkSum` v bajtech.  
  
 `checkSum`  
 pro Vyrovnávací paměť, do které jsou uloženy informace kontrolního součtu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud je metoda úspěšná; v opačném případě E_FAIL nebo nějaký jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedDocumentWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
