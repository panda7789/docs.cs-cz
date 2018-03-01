---
title: "ICLRDataTarget – rozhraní"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 73966ffe89f0e84d5a516f20962472d900332faa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget – rozhraní
Poskytuje metody pro interakci s cílová položka common language runtime (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Získá identifikátor pro aktuální vlákno.|  
|[GetImageBase – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Získá adresu základní paměti pro zadanou bitovou kopii.|  
|[GetMachineType – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Získá identifikátor pro druh sada instrukcí, která používá tento cílový proces.|  
|[GetPointerSize – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Získá velikost v bajtech ukazatel na aktuální cíl.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Získá ukazatel do kontextu vlákno se zadaným identifikátorem.|  
|[GetTLSValue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Získá hodnotu v místní úložiště vláken (TLS) v zadaném indexu pro zadaný vlákno.|  
|[ReadVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Čte data z adresy zadaný virtuální paměti do zadané vyrovnávací paměti.|  
|[Request – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup požádat o operaci podle definice implementace.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Nastaví aktuální kontext zadaný vlákno v tento cílový proces.|  
|[SetTLSValue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Nastaví hodnotu v místní úložiště vláken (TLS) zadaný vlákna v tento cílový proces.|  
|[WriteVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapíše data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní podle potřeby pro konkrétní cílový položku musí implementovat rozhraní API klienta (ladicí program). Například živý proces bude mít jinou implementaci než výpis paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
