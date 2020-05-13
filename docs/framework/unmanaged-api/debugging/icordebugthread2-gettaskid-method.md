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
ms.openlocfilehash: 841af546cc3586529fe290c69e686438f634b90d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377788"
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
 Úloha může být spuštěna pouze ve vlákně, pokud je vlákno přidruženo k připojení. `GetTaskID`vrátí nulu v `pTaskId` případě, že vlákno není přidruženo k připojení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
