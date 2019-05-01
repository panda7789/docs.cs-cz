---
title: ISymUnmanagedWriter::OpenMethod – metoda
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.OpenMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b05ba185a9ad4ab076d29d7d609734d41677b760
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986047"
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod – metoda
Otevře se metoda, do které symbol je vygenerován informace. Dané metody se změní aktuální metoda pro volání zadat body sekvence, parametry a lexikální obory. Existuje implicitní lexikální prostor kolem celou metodu. Znovu metodu, která dříve byla uzavřena vymaže všechny dříve definované symboly pro danou metodu. Najednou lze otevřít pouze jednu metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
## <a name="parameters"></a>Parametry  
 `method`  
 [in] Token metadat pro metodu otevřít.  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud metoda uspěje; S_OK v opačném případě E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také:

- [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [CloseMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)
- [OpenMethod2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
