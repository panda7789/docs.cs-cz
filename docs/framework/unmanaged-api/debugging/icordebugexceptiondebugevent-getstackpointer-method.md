---
title: "ICorDebugExceptionDebugEvent::GetStackPointer – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1b9096bbb494036156a528d8f9e940630f555f6a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a>ICorDebugExceptionDebugEvent::GetStackPointer – metoda
Získá ukazatel zásobníku pro tuto událost výjimky ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStackPointer`  
 [out] Ukazatel na adresu ukazatel zásobníku pro výjimku ladění událostí. Další informace naleznete v části Poznámky.  
  
## <a name="remarks"></a>Poznámky  
 Význam tento ukazatel zásobníku závisí na typu události, jak je znázorněno v následující tabulce.  
  
|Typ události|Význam `pStackPointer` hodnota|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Ukazatel zásobníku pro rámečku, která vrátila výjimku.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Ukazatel zásobníku pro na uživatelském kódu rámce nejbližší bod vyvolaná výjimka.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|Ukazatel zásobníku pro rámce, který obsahuje obslužná rutina catch.|  
|[MANAGED_EXCEPTION_UNHANDLED](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|`pStackPointer`je **null**.|  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
 Typ události má k dispozici [icordebugdebugevent::geteventkind –](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugExceptionDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
