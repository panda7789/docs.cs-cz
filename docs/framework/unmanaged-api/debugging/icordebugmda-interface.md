---
title: ICorDebugMDA – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cea8f6827d3e361b3f6498e6612d8b11a2357285
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916666"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA – rozhraní
Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDescription – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|Získá řetězec obsahující popis toto MDA.|  
|[GetFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|Získá příznaky spojené se toto MDA.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|Získá řetězec obsahující název toto MDA.|  
|[GetOSThreadId – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|Získá identifikátor vlákna operačního systému, na kterém je spuštěn toto MDA.|  
|[GetXML – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|Získá úplný datový proud XML spojené s toto MDA.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
