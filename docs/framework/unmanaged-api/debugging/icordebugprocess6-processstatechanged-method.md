---
title: "ICorDebugProcess6::ProcessStateChanged – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e5aad3e95668525fe607bf4e90b4e05b2b58cad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged – metoda
Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kterém proces běží.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
#### <a name="parameters"></a>Parametry  
 `change`  
 [v] Člen [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) – výčet  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volá tuto metodu za účelem oznámit [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kterém proces běží.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
