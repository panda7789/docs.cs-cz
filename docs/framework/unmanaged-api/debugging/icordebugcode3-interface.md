---
title: "ICorDebugCode3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugCode3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugCode3
helpviewer_keywords: ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a89bc2b516f87a4deb7ccb794b5ae0352d6a8efc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 – rozhraní
Poskytne metodu, která rozšiřuje "ICorDebugCode" a "Icordebugcode2 –" k zadání informací o spravovaných návratovou hodnotu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetReturnValueLiveOffset – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|Pro zadaný korekce IL získá nativní posuny, kde má být umístěn zarážku tak, aby ladicí program můžete získat návratovou hodnotou z funkce.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
    
    
    
 [ICorDebugILFrame3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
