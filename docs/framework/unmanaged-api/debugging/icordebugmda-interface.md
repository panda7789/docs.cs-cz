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
ms.openlocfilehash: d711f36b4e2071dac9458a023e1d3cf4743e77b3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212630"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA – rozhraní
Představuje zprávu pomocníka spravovaného ladění (MDA).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetDescription – metoda](icordebugmda-getdescription-method.md)|Získá řetězec obsahující popis tohoto typu MDA.|  
|[GetFlags – metoda](icordebugmda-getflags-method.md)|Získá příznaky přidružené k tomuto MDA.|  
|[GetName – metoda](icordebugmda-getname-method.md)|Získá řetězec obsahující název této aplikace MDA.|  
|[GetOSThreadId – metoda](icordebugmda-getosthreadid-method.md)|Získá identifikátor vlákna operačního systému, na kterém je tento MDA spuštěn.|  
|[GetXML – metoda](icordebugmda-getxml-method.md)|Získá úplný datový proud XML přidružený k tomuto MDA.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
