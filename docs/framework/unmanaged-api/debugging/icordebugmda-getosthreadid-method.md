---
title: "ICorDebugMDA::GetOSThreadId – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugMDA.GetOSThreadId
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6cc53eecadd982d7cea045424de52d8e6f64107b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId – metoda
Získá identifikátor operační systém (OS) přístup z více vláken, na kterém reprezentována Pomocník spravovaného ladění (MDA) [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) spouští.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pOsTid`  
 [out] Ukazatel na identifikátor operačního systému.  
  
## <a name="remarks"></a>Poznámky  
 Vlákno operačního systému se používá namísto ICorDebugThread pro situace, ve kterých je spouštěna MDA nativní vlákno buď spravovaných vláken, který ještě nebyl zadán spravovaného kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMDA – rozhraní rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
