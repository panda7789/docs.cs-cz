---
title: ICorConfiguration – rozhraní
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763266"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration – rozhraní
Poskytuje metody pro konfiguraci common language runtime (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddDebuggerSpecialThread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Ladění služeb označuje, že konkrétní vlákno by měla být povolena má pokračovat provedením zatímco ladicí program zastavuje během scénáře ladění spravované nebo nespravované aplikace.|  
|[SetDebuggerThreadControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Nastaví rozhraní zpětného volání, které služeb ladění bude volat vlákna modulu CLR jsou blokované a odblokováno pro ladění.|  
|[SetGCHostControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Nastaví rozhraní zpětného volání systému uvolňování paměti používané k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.|  
|[SetGCThreadControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Nastaví rozhraní zpětného volání pro plánování vláken pro úlohy – modul runtime, které by se jinak zablokovaly pro uvolnění paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
