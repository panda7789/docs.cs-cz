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
ms.openlocfilehash: f7635dc3fad9b3de30fa052c7d2e67a7e6953fb3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789046"
---
# <a name="iclrdatatarget3-interface"></a>ICLRDataTarget3 – rozhraní
Podtřída [ICLRDataTarget2](iclrdatatarget2-interface.md) , která poskytuje přístup k informacím o výjimce.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetExceptionRecord – metoda](iclrdatatarget3-getexceptionrecord-method.md)|Je volána službami modulu Common Language Runtime (CLR) pro přístup k datům za účelem získání záznamu o výjimce související s cílovým procesem.|  
|[GetExceptionContextRecord – metoda](iclrdatatarget3-getexceptioncontextrecord-method.md)|Je volána službami modulu CLR pro přístup k datům za účelem získání záznamu o kontextu souvisejícím s cílovým procesem.|  
|[GetExceptionThreadID – metoda](iclrdatatarget3-getexceptionthreadid-method.md)|Volá se službami CLR Data Access, aby získaly ID vlákna, které vyvolalo výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Klient API (tzn. ladicí program) musí implementovat toto rozhraní v závislosti na konkrétním cílovém procesu. Například živý proces bude mít jinou implementaci než výpis paměti. Cíl nemusí podporovat změny jeho oblastí paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget – rozhraní](iclrdatatarget-interface.md)
- [ICLRDataTarget2 – rozhraní](iclrdatatarget2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
