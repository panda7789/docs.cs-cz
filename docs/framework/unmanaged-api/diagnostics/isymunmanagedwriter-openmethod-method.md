---
title: "ISymUnmanagedWriter::OpenMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.OpenMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::OpenMethod
helpviewer_keywords:
- ISymUnmanagedWriter::OpenMethod method [.NET Framework debugging]
- OpenMethod method [.NET Framework debugging]
ms.assetid: fb90cb7f-af88-45e8-a99f-80a0bbddb08b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6cfb41748861150b28493c835e80135abe90826
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriteropenmethod-method"></a>ISymUnmanagedWriter::OpenMethod – metoda
Otevře se metoda, do které symbol informace jsou vydávány. Aktuální metoda pro volání zadat body sekvence, parametry a lexikální obory se změní na dané metody. Existuje implicitní lexikální prostor kolem celého metoda. Znovu metodu, která byla dříve uzavřený vymaže všechny dříve definovaném symboly pro danou metodu. Současně lze otevřít pouze jednu metodu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenMethod(  
    [in] mdMethodDef method);  
```  
  
#### <a name="parameters"></a>Parametry  
 `method`  
 [v] Token metadata pro metodu chcete otevřít.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [CloseMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)  
 [OpenMethod2 – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-openmethod2-method.md)
