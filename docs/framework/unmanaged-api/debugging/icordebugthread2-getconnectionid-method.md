---
title: ICorDebugThread2::GetConnectionID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138688"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID – metoda
Získá identifikátor připojení pro tento objekt ICorDebugThread2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwConnectionId`  
 mimo `CONNID`, který představuje identifikátor připojení.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetConnectionID` vrátí nulu v parametru `pdwConnectionId`, pokud toto vlákno není součástí připojení.  
  
 Pokud je toto vlákno připojeno k instanci Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` se mapuje na identifikátor procesu serveru (SPID).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
