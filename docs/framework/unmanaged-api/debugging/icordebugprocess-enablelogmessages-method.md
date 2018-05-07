---
title: ICorDebugProcess::EnableLogMessages – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0dbac6570fc0af0452a0e44f838124afbf6a4fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessenablelogmessages-method"></a>ICorDebugProcess::EnableLogMessages – metoda
Povolí nebo zakáže přenos zpráv protokolu pro ladicí program.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fOnOff`  
 [v] `true` umožňuje přenos zpráv protokolu; `false` zakáže přenos.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je platná pouze po [icordebugmanagedcallback::CreateProcess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md) dojde k zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
