---
title: "INotifySink2::OnSyncCallEnter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 102a4a24b82c87bed00895dc723b7fca02c20bcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallenter-method"></a>INotifySink2::OnSyncCallEnter – metoda
Získá volána při zadávání volání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `in_CallID`  
 [v] ID volání jejich zadání. V tématu [CALL_ID – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `in_pBuffer`  
 [v] Volání vyrovnávací paměti.  
  
 `in_BufferSize`  
 [v] Velikost vyrovnávací paměti volání, v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
