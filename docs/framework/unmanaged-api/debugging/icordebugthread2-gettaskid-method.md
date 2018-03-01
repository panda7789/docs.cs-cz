---
title: "ICorDebugThread2::GetTaskID – metoda"
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
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1b94478a0dfb8cc4d90dea611620238024634799
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID – metoda
Získá identifikátor úloha spuštěná na tento přístup z více vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTaskId`  
 [out] Ukazatel na identifikátor úloha spuštěná na vlákno představuje tento objekt icordebugthread2 –.  
  
## <a name="remarks"></a>Poznámky  
 Úloha může být spuštěn ve vlákně pouze, pokud vlákno je přidružené k připojení. `GetTaskID`Vrátí hodnotu hodnotu `pTaskId` Pokud vlákno není přidružené k připojení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
