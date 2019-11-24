---
title: ISymUnmanagedBinder::GetReaderFromStream – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
ms.openlocfilehash: b1cb2bf3aa021ed738f7fad93fc4b86d97baf1e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449389"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream – metoda
Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a>Parametry  
 `importer`  
 [in] A pointer to the metadata import interface.  
  
 `pstream`  
 [in] A pointer to the stream that contains the symbol store.  
  
 `pRetVal`  
 [out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK if the method succeeds; otherwise, E_FAIL or some other error code.  
  
## <a name="requirements"></a>Požadavky  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
