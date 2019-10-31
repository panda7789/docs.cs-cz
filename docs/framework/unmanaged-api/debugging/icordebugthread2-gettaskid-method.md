---
title: ICorDebugThread2::GetTaskID – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: d5f2838007504e56ad44614a6778083be046629f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140082"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID – metoda
Získá identifikátor úlohy spuštěné v tomto vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTaskId`  
 mimo Ukazatel na identifikátor úlohy spuštěné ve vlákně reprezentované tímto objektem ICorDebugThread2.  
  
## <a name="remarks"></a>Poznámky  
 Úloha může být spuštěna pouze ve vlákně, pokud je vlákno přidruženo k připojení. `GetTaskID` vrátí nulu v `pTaskId`, pokud vlákno není přidruženo k připojení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
