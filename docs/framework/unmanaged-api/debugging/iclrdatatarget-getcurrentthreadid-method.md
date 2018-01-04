---
title: "ICLRDataTarget::GetCurrentThreadID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.GetCurrentThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2fd2c39b20b823e18232081d1655a6770bafccc5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a>ICLRDataTarget::GetCurrentThreadID – metoda
Získá identifikátor pro aktuální vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [out] Ukazatel na identifikátor operační systém aktuální vlákno pro tento cílový proces.  
  
## <a name="remarks"></a>Poznámky  
 Pokud není žádná aktuální vlákno pro tento cílový proces `GetCurrentThreadID` metoda může selhat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
