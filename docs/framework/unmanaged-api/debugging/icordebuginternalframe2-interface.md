---
title: "ICorDebugInternalFrame2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2
helpviewer_keywords: ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d87303fbe95804b458a42ed43b65f29233814977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2-interface"></a>ICorDebugInternalFrame2 – rozhraní
Poskytuje informace o interní rámce, včetně adres zásobníku a pozice ve vztahu k ICorDebugFrame objekty.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetFrameAddress – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|Vrátí adresu zásobníku vnitřní rámečku.|  
|[IsCloserToLeaf – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|Kontroluje, zda `this` interní rámečku je blíž ke listu než zadaný objekt ICorDebugFrame.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní rozšiřuje icordebuginternalframe – rozhraní.  
  
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
