---
title: "ISymUnmanagedBinder::GetReaderFromStream – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36d4d0067cd638eb39ce82eb042242b7b08d3647
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a>ISymUnmanagedBinder::GetReaderFromStream – metoda
Zadaný datový proud, který obsahuje úložiště symbolů a metadat rozhraní, vrátí správné [ISymUnmanagedReader](isymunmanagedreader-interface.md) struktura, která budou číst ladění symboly z obchodu daný symbol.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `importer`  
 [v] Ukazatel rozhraní import metadat.  
  
 `pstream`  
 [v] Ukazatel na datový proud, který obsahuje úložiště symbolů.  
  
 `pRetVal`  
 [out] Ukazatele, který je nastavený s vráceným [ISymUnmanagedReader](isymunmanagedreader-interface.md) rozhraní.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedBinder – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
