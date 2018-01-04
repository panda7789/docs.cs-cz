---
title: "ISymUnmanagedScope::GetLocalCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope.GetLocalCount
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope::GetLocalCount
helpviewer_keywords:
- GetLocalCount method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocalCount method [.NET Framework debugging]
ms.assetid: 3ede8fb5-f655-4088-8e19-9c53812588a8
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9db774140ef55b2dfcb54ff701c2b842418a4923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscopegetlocalcount-method"></a>ISymUnmanagedScope::GetLocalCount – metoda
Získá počet místní proměnné definované v tomto rozsahu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalCount(  
    [out, retval] ULONG32 *pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 [out] Ukazatel na `ULONG32` která přijme počet lokální proměnné.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda úspěšně. v opačném E_FAIL nebo jiný kód chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedScope – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
