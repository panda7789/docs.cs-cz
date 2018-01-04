---
title: "ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d5f88656-433d-447c-b21c-2a12bed2e72a
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 96040ee5f56ade3647367c4b879c8aa9e7f460fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodgetcatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethod::GetCatchHandlerILOffset – metoda
V tématu [definecatchhandleriloffset – metoda](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT GetCatchHandlerILOffset(    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---------------|-----------------|  
|`pRetVal`||  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí `HRESULT`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Viz také  
 [ISymUnmanagedAsyncMethod – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)
