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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c0e76b179854a380e66ac9daedffa8ccf4aa4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
