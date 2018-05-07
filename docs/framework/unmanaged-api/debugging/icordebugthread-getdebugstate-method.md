---
title: ICorDebugThread::GetDebugState – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95d9696e29bc1b460c94d7f4d8afd3de82653333
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState – metoda
Získá aktuální stav tohoto objektu ICorDebugThread ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pState`  
 [out] Ukazatel na bitovou kombinaci CorDebugThreadState – výčet hodnot, které popisují aktuální stav ladění tohoto podprocesu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud tento proces je nyní zastavena, `pState` představuje stav ladění, které by existovat pro tento přístup z více vláken, pokud proces dál, nikoli skutečné aktuální stav tohoto podprocesu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
