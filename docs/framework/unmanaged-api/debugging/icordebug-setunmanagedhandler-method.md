---
title: "ICorDebug::SetUnmanagedHandler – metoda"
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
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c1b6da9db047321583de8c3c9238ed9ad4d4ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler – metoda
Určuje objekt obslužné rutiny události pro události se nespravované.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [v] Ukazatel na [icordebugunmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objekt, který reprezentuje obslužnou rutinu události pro nespravované události.  
  
## <a name="remarks"></a>Poznámky  
 Obslužné rutiny události objektu pro nespravované události musí být nastavena po volání [icordebug::Initialize –](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) a před volání [icordebug::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) nebo [icordebug::DebugActiveProcess – ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). Pro starší verze účely, ale není nutné nastavit objekt obslužné rutiny události pro nespravované události, dokud první nativní ladění událost se vyvolá. Konkrétně Pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED nativní ladění události nelze odeslat, dokud je obnoveno hlavního vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
