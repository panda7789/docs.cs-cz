---
title: "ICorDebugProcess2::GetThreadForTaskID – metoda"
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
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af63e6cf0d7e4b51f9365c1ccc4ac78158c091bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a>ICorDebugProcess2::GetThreadForTaskID – metoda
Získá vláken, na kterém je prováděna úloha se zadaným identifikátorem.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `taskid`  
 [v] Identifikátor úlohy.  
  
 `ppThread`  
 [out] Ukazatel na adresu icordebugthread2 – objekt, který představuje vlákno, které mají být načteny.  
  
## <a name="remarks"></a>Poznámky  
 Hostitele lze nastavit identifikátor úlohy pomocí [iclrtask::settaskidentifier –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-settaskidentifier-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
