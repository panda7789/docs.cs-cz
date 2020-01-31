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
ms.openlocfilehash: 2b5c99e40aabdbc654bdc612729b2756e3ef5bb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793719"
---
# <a name="iclrdatatarget-interface"></a>ICLRDataTarget – rozhraní
Poskytuje metody pro interakci s cílovou položkou modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCurrentThreadID – metoda](iclrdatatarget-getcurrentthreadid-method.md)|Načte identifikátor operačního systému pro aktuální vlákno.|  
|[GetImageBase – metoda](iclrdatatarget-getimagebase-method.md)|Načte základní adresu paměti pro zadanou bitovou kopii.|  
|[GetMachineType – metoda](iclrdatatarget-getmachinetype-method.md)|Získá identifikátor pro druh sady instrukcí, které cílový proces používá.|  
|[GetPointerSize – metoda](iclrdatatarget-getpointersize-method.md)|Získá velikost ukazatele na aktuální cíl v bajtech.|  
|[GetThreadContext – metoda](iclrdatatarget-getthreadcontext-method.md)|Získá ukazatel na kontext vlákna se zadaným identifikátorem.|  
|[GetTLSValue – metoda](iclrdatatarget-gettlsvalue-method.md)|Získá hodnotu v thread local Storage (TLS) v zadaném indexu pro zadané vlákno.|  
|[ReadVirtual – metoda](iclrdatatarget-readvirtual-method.md)|Načte data ze zadané adresy virtuální paměti do zadané vyrovnávací paměti.|  
|[Request – metoda](iclrdatatarget-request-method.md)|Volá se službami CLR (Common Language Runtime) k vyžádání operace, jak jsou definované implementací.|  
|[SetThreadContext – metoda](iclrdatatarget-setthreadcontext-method.md)|Nastaví aktuální kontext zadaného vlákna v cílovém procesu.|  
|[SetTLSValue – metoda](iclrdatatarget-settlsvalue-method.md)|Nastaví hodnotu v thread local Storage (TLS) zadaného vlákna v cílovém procesu.|  
|[WriteVirtual – metoda](iclrdatatarget-writevirtual-method.md)|Zapisuje data ze zadané vyrovnávací paměti do zadané adresy virtuální paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Klient rozhraní API (to znamená ladicí program) musí implementovat toto rozhraní, jak je to vhodné pro konkrétní cílovou položku. Například živý proces bude mít jinou implementaci než výpis paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataTarget2 – rozhraní](iclrdatatarget2-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
