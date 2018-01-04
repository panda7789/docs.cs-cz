---
title: "INotifySink2::OnSyncCallOut – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: INotifySink2.OnSyncCallOut
api_location: diasymreader.dll
api_type: COM
f1_keywords: INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 484027fe0ab8e5e416059678d2603080ed730be3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inotifysink2onsynccallout-method"></a>INotifySink2::OnSyncCallOut – metoda
Získá volá při volání je limit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `in_CallID`  
 [v] ID hovoru, který je na. V tématu [CALL_ID – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).  
  
 `out_ppBuffer`  
 [out] Volání vyrovnávací paměti.  
  
 `out_pBufferSize`  
 [out] Velikost vyrovnávací paměti volání, v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK, pokud metoda bude úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>Viz také  
 [INotifySink2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [INotifySource2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [INotifyConnection2 – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
