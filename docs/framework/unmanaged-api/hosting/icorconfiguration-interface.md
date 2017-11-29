---
title: "ICorConfiguration – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorConfiguration
helpviewer_keywords: ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6bc66abf28e90d858d993bd62e9c67f840af137b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration – rozhraní
Poskytuje metody pro konfiguraci common language runtime (CLR).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Adddebuggerspecialthread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|K ladění služby označuje, že konkrétní vlákno by měl povolit chcete pokračovat v provádění ladicí program se zastavila během ladění scénáře spravované nebo nespravované aplikace.|  
|[Setdebuggerthreadcontrol – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Nastaví zpětné volání rozhraní, které ladění služby bude volat jako CLR vláken je blokovaný a odblokováno pro ladění.|  
|[Setgchostcontrol – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Nastaví zpětné volání rozhraní, které chcete použít modulem garbage collector k vyžádání hostitele, chcete-li změnit omezení virtuální paměti.|  
|[Setgcthreadcontrol – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Nastaví zpětné volání rozhraní pro plánování vláken pro úlohy – modul runtime, které by jinak blokovaly pro uvolnění paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Corruntimehost – třída typu Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
