---
title: Icordebughandlevalue – Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed6ba8a738b4086b9150e0a1c7b300a519fa3092
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419104"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
