---
title: "ICorDebugThread2::GetConnectionID – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28fa949de768191061bd747034a5c951a03b8596
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID – metoda
Získá identifikátor připojení pro tento objekt icordebugthread2 –.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwConnectionId`  
 [out] A `CONNID` představující identifikátor připojení.  
  
## <a name="remarks"></a>Poznámky  
 `GetConnectionID` Metoda vrátí hodnotu nula v `pdwConnectionId` parametr, pokud tohoto podprocesu není součástí připojení.  
  
 Pokud tento přístup z více vláken je připojen k instanci systému Microsoft SQL Server 2005 Analysis Services (SSAS), `CONNID` mapuje identifikátor procesu serveru (SPID).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
