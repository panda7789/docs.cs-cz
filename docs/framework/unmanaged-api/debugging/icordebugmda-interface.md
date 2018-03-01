---
title: "ICorDebugMDA – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9c53e03acddc5d732a684cf825bce49a65bb4c31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA – rozhraní
Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDescription – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Získá řetězec, který obsahuje popis této (mda).|  
|[GetFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Získá příznaky přidružené k této (mda).|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Získá řetězec, který obsahuje název této (mda).|  
|[GetOSThreadId – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Získá identifikátor operačního systému přístup z více vláken, na kterém je tento MDA provádění.|  
|[GetXML – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Získá úplný datový proud XML přidružené k této (mda).|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
