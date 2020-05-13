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
ms.openlocfilehash: b8d20de990ff4a27a82590342494a307c986457e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207397"
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
 Před voláním metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) volejte tuto metodu, pokud vlákno oznámilo nespravovanou výjimku, kterou by měl ignorovat laděného procesu. Tím se v daném vláknu vymažou nedokončené události v pásmu (IB) i mimo pásmo (OOB). Všechny zarážky OOB a výjimky s jedním krokem se automaticky vymažou.  
  
 K zachycení aktuální spravované výjimky ve vlákně použijte [ICorDebugThread2:: InterceptCurrentException –](icordebugthread2-interceptcurrentexception-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
