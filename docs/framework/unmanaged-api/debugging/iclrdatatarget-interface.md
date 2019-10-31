---
title: ICLRDataTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget
helpviewer_keywords:
- ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type:
- apiref
ms.openlocfilehash: 51b246e45b8bbdf809f5e90ac2bc29ca724751fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73113492"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget – rozhraní
Poskytuje metody pro interakci s cílovou položkou modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Načte identifikátor operačního systému pro aktuální vlákno.|  
|[GetImageBase – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Načte základní adresu paměti pro zadanou bitovou kopii.|  
|[GetMachineType – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Získá identifikátor pro druh sady instrukcí, které cílový proces používá.|  
|[GetPointerSize – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Získá velikost ukazatele na aktuální cíl v bajtech.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Získá ukazatel na kontext vlákna se zadaným identifikátorem.|  
|[GetTLSValue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Získá hodnotu v thread local Storage (TLS) v zadaném indexu pro zadané vlákno.|  
|[ReadVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Načte data ze zadané adresy virtuální paměti do zadané vyrovnávací paměti.|  
|[Request – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Nastaví aktuální kontext zadaného vlákna v cílovém procesu.|  
|[SetTLSValue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Nastaví hodnotu v thread local Storage (TLS) zadaného vlákna v cílovém procesu.|  
|[WriteVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapisuje data ze zadané vyrovnávací paměti do zadané adresy virtuální paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Klient rozhraní API (to znamená ladicí program) musí implementovat toto rozhraní, jak je to vhodné pro konkrétní cílovou položku. Například živý proces bude mít jinou implementaci než výpis paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
