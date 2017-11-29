---
title: ICorDebugObjectValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue
helpviewer_keywords: ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: acbfbbb8f7374b1ab783371d318bd3bcf89963fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugobjectvalue-interface1"></a>ICorDebugObjectValue Interface1
Podtřídou třídy "ICorDebugValue", který představuje hodnotu, která obsahuje objekt.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Getclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md)|Získá ukazatele rozhraní do common language runtime (CLR) <xref:System.Type> objektu, který tato `ICorDebugObjectValue` odkazy.|  
|[Getcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getcontext-method.md)|Není implementováno.|  
|[GetFieldValue – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getfieldvalue-method.md)|Získá ukazatele rozhraní k [ICorDebugValue](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-interface.md) představující hodnotu zadaného pole pro zadanou třídu.|  
|[Getmanagedcopy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getmanagedcopy-method.md)|Zastaralé. Tato metoda není volána.|  
|[Getvirtualmethod – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getvirtualmethod-method.md)|Není implementováno.|  
|[Isvalueclass – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-isvalueclass-method.md)|Získá hodnotu, která určuje, zda objekt odkazuje toto `ICorDebugObjectValue` je typ hodnoty.|  
|[Setfrommanagedcopy – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-setfrommanagedcopy-method.md)|Zastaralé. Tato metoda není volána.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugObjectValue` Zůstane platná, dokud proces laděné pokračuje.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 
