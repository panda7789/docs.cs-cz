---
title: "ICLRDataTarget – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget
helpviewer_keywords: ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: e2f05155-9bef-4e11-b703-7f05890665ca
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6a40276b28f3d20428f0d7eb0556a762fdb56801
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget – rozhraní
Poskytuje metody pro interakci s cílová položka common language runtime (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentThreadId – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Získá identifikátor pro aktuální vlákno.|  
|[Getimagebase – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Získá adresu základní paměti pro zadanou bitovou kopii.|  
|[Getmachinetype – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Získá identifikátor pro druh sada instrukcí, která používá tento cílový proces.|  
|[Getpointersize – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Získá velikost v bajtech ukazatel na aktuální cíl.|  
|[Getthreadcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Získá ukazatel do kontextu vlákno se zadaným identifikátorem.|  
|[Gettlsvalue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Získá hodnotu v místní úložiště vláken (TLS) v zadaném indexu pro zadaný vlákno.|  
|[Readvirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Čte data z adresy zadaný virtuální paměti do zadané vyrovnávací paměti.|  
|[Request – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup požádat o operaci podle definice implementace.|  
|[Setthreadcontext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Nastaví aktuální kontext zadaný vlákno v tento cílový proces.|  
|[Settlsvalue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Nastaví hodnotu v místní úložiště vláken (TLS) zadaný vlákna v tento cílový proces.|  
|[Writevirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapíše data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní podle potřeby pro konkrétní cílový položku musí implementovat rozhraní API klienta (ladicí program). Například živý proces bude mít jinou implementaci než výpis paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrdatatarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
