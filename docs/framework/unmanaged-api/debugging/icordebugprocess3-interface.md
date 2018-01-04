---
title: "ICorDebugProcess3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess3
helpviewer_keywords: ICorDebugProcess3 interface [.NET Framework debugging]
ms.assetid: ced9c82e-d7b0-4806-a151-98b6611d3097
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 894d3295b83a1971792e6da845f276be486a4ea5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess3-interface"></a>ICorDebugProcess3 – rozhraní
Řídí vlastní oznámení ladicího programu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SetEnableCustomNotification – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-setenablecustomnotification-method.md)|Povolí nebo zakáže oznámení vlastní ladicí program zadaného typu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní logicky rozšiřuje ICorDebugProcess a icordebugprocess2 – rozhraní.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
