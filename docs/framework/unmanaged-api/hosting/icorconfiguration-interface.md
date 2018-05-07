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
ms.openlocfilehash: 63699f0af69b3a7623c5e9da156c2ff8ae83ccfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration – rozhraní
Poskytuje metody pro konfiguraci common language runtime (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddDebuggerSpecialThread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|K ladění služby označuje, že konkrétní vlákno by měl povolit chcete pokračovat v provádění ladicí program se zastavila během ladění scénáře spravované nebo nespravované aplikace.|  
|[SetDebuggerThreadControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Nastaví zpětné volání rozhraní, které ladění služby bude volat jako CLR vláken je blokovaný a odblokováno pro ladění.|  
|[SetGCHostControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Nastaví zpětné volání rozhraní, které chcete použít modulem garbage collector k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.|  
|[SetGCThreadControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Nastaví zpětné volání rozhraní pro plánování vláken pro úlohy – modul runtime, které by jinak blokovaly pro uvolnění paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CorRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
