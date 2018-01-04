---
title: "ISymUnmanagedWriter3::OpenMethod2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter3.OpenMethod2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8da6de0271ddce5b956e667420a206c09cc291d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter3openmethod2-method"></a>ISymUnmanagedWriter3::OpenMethod2 – metoda
Otevře metodu a poskytuje její skutečné části posun v bitové kopii.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OpenMethod2(   
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
#### <a name="parameters"></a>Parametry  
 `method`  
 [v] Token metadata pro metodu chcete otevřít.  
  
 `isect`  
 [v] Část posun v bitové kopii.  
  
 `offset`  
 [v] Posun v bitové kopii.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedWriter3 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 [OpenMethod – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
