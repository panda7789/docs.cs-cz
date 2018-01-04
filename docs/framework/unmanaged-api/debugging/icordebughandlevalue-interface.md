---
title: "Icordebughandlevalue – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHandleValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHandleValue
helpviewer_keywords: ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8df7b46bf22fa1a3a8633cbad7ad1a6582b4860
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebughandlevalue-interface1"></a>Icordebughandlevalue – Interface1
Podtřídou třídy ICorDebugReferenceValue, který představuje hodnotu odkaz, ke kterému ladicí program vytvořil popisovač pro uvolňování paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Dispose – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Uvolní popisovač odkazuje toto `ICorDebugHandleValue` objekt explicitně stisknutým ukazatel rozhraní.|  
|[GetHandleType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Získá hodnotu CorDebugHandleType, která popisuje typ popisovače odkazuje toto `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugReferenceValue` Objekt zneplatněna mezerou v provádění vyladěnou kódu. `ICorDebugHandleValue` Udržuje odkaz na jeho prostřednictvím zalomení a pokračování, dokud ji explicitně vydání.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
