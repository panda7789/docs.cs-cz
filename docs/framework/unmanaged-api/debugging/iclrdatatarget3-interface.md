---
title: ICLRDataTarget3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54d6535e2b2c4761eb3c67a990c62f2c311cf133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 – rozhraní
Podtřídou třídy [iclrdatatarget2 –](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , který poskytuje přístup k informacím o výjimce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetExceptionRecord – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.|  
|[GetExceptionContextRecord – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|Je volána službami modulu CLR pro přístup k datům za účelem získání záznamu o kontextu souvisejícím s cílovým procesem.|  
|[GetExceptionThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|Voláno rozhraním služby CLR data přístup získat ID podprocesu, která vrátila výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu. Například živý proces bude mít jinou implementaci než výpis paměti. Cíl nemusí podporovat změny jeho oblastí paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
