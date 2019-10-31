---
title: ICorDebugProcess::ClearCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 37a7d8fa4439d52db3cddfff22ac6580b19af58a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128917"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException – metoda
Vymaže aktuální nespravovanou výjimku na daném vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 pro ID vlákna, na kterém bude vymazána aktuální nespravovanou výjimka.  
  
## <a name="remarks"></a>Poznámky  
 Před voláním metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) volejte tuto metodu, pokud vlákno oznámilo nespravovanou výjimku, kterou by měl ignorovat laděného procesu. Tím se v daném vláknu vymažou nedokončené události v pásmu (IB) i mimo pásmo (OOB). Všechny zarážky OOB a výjimky s jedním krokem se automaticky vymažou.  
  
 K zachycení aktuální spravované výjimky ve vlákně použijte [ICorDebugThread2:: InterceptCurrentException –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
