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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1272df17a9a9a500b84f62914811b8d109bf3cdd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768950"
---
# <a name="icordebugthread2gettaskid-method"></a>ICorDebugThread2::GetTaskID – metoda
Získá identifikátor úloha spuštěná na toto vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTaskId`  
 [out] Ukazatel na identifikátor úloha spuštěná na vlákno reprezentovaný tímto objektem icordebugthread2 –.  
  
## <a name="remarks"></a>Poznámky  
 Úkol může být spuštěn ve vlákně pouze, pokud vlákno je spojen s připojením. `GetTaskID` Vrátí nulu `pTaskId` Pokud vlákno není přidružen k připojení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
