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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ed3cb62b56e80a7fe4ea54b43ac9f4a28b8d102
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100246"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget – rozhraní
Poskytuje metody pro interakci s cílová položka modulu common language runtime (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentThreadID – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getcurrentthreadid-method.md)|Získá identifikátor operačního systému pro aktuální vlákno.|  
|[GetImageBase – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getimagebase-method.md)|Získá adresu základní paměti pro zadané bitové kopie.|  
|[GetMachineType – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getmachinetype-method.md)|Získá identifikátor pro typ instrukční sadu, která používá cílového procesu.|  
|[GetPointerSize – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getpointersize-method.md)|Získá velikost v bajtech, ukazatele na aktuálním cíli.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-getthreadcontext-method.md)|Získá ukazatel na kontext vlákna se zadaným identifikátorem.|  
|[GetTLSValue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-gettlsvalue-method.md)|Získá hodnotu, v místním úložišti vláken (TLS) v zadaném indexu pro zadaný podproces.|  
|[ReadVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-readvirtual-method.md)|Načte data z adresy zadaná virtuální paměti do zadané vyrovnávací paměti.|  
|[Request – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-request-method.md)|Voláno rozhraním common language runtime (CLR) data access services požádat o operaci, jak je definováno implementací.|  
|[SetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-setthreadcontext-method.md)|Nastaví aktuální kontext ze zadaného vlákna v cílovém procesu.|  
|[SetTLSValue – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-settlsvalue-method.md)|Nastaví hodnotu v místním úložišti vláken (TLS) ze zadaného vlákna v cílovém procesu.|  
|[WriteVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-writevirtual-method.md)|Zapisuje data ze zadané vyrovnávací paměti na adresu zadanou virtuální paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Klient API (ladicí program) musí implementovat toto rozhraní podle potřeby pro konkrétní cílovou položku. Například živý proces bude mít jinou implementaci než výpis paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
