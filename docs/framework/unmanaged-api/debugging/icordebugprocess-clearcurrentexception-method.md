---
title: "ICorDebugProcess::ClearCurrentException – metoda"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 905ade7e5c44861b4ad6e7eb57fe7d3e3e9e3002
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException – metoda
Vymaže aktuální nespravované výjimky na dané vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [v] ID podprocesu, na kterém se vymaže aktuální nespravované výjimky.  
  
## <a name="remarks"></a>Poznámky  
 Volat tuto metodu před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) při vlákno ohlásil nespravované výjimka, která má být ignorována ladění. Tímto dojde k vymazání nezpracovaných integrované (IB) i out-of-band události (OOB) na dané vlákno. Všechny OOB zarážky a krokování výjimky jsou automaticky vymazány.  
  
 Použití [icordebugthread2::interceptcurrentexception –](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) zachytávat aktuální spravované výjimky na vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
