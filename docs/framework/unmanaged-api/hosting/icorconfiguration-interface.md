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
ms.openlocfilehash: 80bb68486e555d6c96cf8ee56ed6d60e41c7c5c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127806"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration – rozhraní
Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddDebuggerSpecialThread – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|Označuje ladicí služby, že by mělo být povoleno pokračování v provádění určitého vlákna, zatímco ladicí program aplikace zastavil během spravovaných nebo nespravovaných scénářů ladění.|  
|[SetDebuggerThreadControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|Nastaví rozhraní zpětného volání, které budou ladit služby volání jako vlákna CLR, jsou blokovány a odblokovány pro ladění.|  
|[SetGCHostControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|Nastaví rozhraní zpětného volání, které má systém uvolňování paměti použít k vyžádání hostitele, aby změnil limity virtuální paměti.|  
|[SetGCThreadControl – metoda](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|Nastaví rozhraní zpětného volání pro plánování vláken pro neběhové úlohy, které by jinak bylo zablokováno pro uvolňování paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
