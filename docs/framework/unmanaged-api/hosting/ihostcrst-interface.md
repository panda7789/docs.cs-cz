---
title: IHostCrst – rozhraní
ms.date: 03/30/2017
api_name:
- IHostCrst
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst
helpviewer_keywords:
- IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type:
- apiref
ms.openlocfilehash: 108492ba298e9f8429b2acd890ab3404365bc602
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130528"
---
# <a name="ihostcrst-interface"></a>IHostCrst – rozhraní
Slouží jako reprezentace kritické části pro vlákno.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Enter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Vstupuje do kritické části.|  
|[Leave – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Ponechá oddíl kritické.|  
|[SetSpinCount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Nastaví počet číselníků pro kritickou část.|  
|[TryEnter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Pokusí se zadat kritickou část a okamžitě nahlásit úspěšnost nebo selhání.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostCrst` umožňuje modulu CLR (Common Language Runtime) komunikovat přímo s reprezentací hostitele kritického oddílu namísto použití funkcí Win32, jako je `EnterCriticalSection` nebo `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
