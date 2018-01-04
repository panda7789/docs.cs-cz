---
title: "ICorDebugBlockingObjectEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum
helpviewer_keywords: ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d35d4ee2ce3c1b7b0f54d78dba8b8639c522d509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugblockingobjectenum-interface"></a>ICorDebugBlockingObjectEnum – rozhraní
Poskytuje enumerátor pro seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury. Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|Vytvoří výčet prostřednictvím seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.|  
  
## <a name="remarks"></a>Poznámky  
 Každý `CorDebugBlockingObject` struktura představuje objekt, který je blokování vlákna.  
  
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
