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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 939f100e8ee386642a29c33827a8339caf0467b9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193184"
---
# <a name="ihostcrst-interface"></a>IHostCrst – rozhraní
Slouží jako hostitele reprezentace kritický oddíl pro dělení na vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Enter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Zadá kritický oddíl.|  
|[Leave – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Ponechá kritický oddíl.|  
|[SetSpinCount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Nastaví počet typu číselník pro kritický oddíl.|  
|[TryEnter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Pokusy o zadání kritický oddíl a sestavy úspěch nebo neúspěch okamžitě.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostCrst` Umožňuje common language runtime (CLR) přímo komunikovat s hostitele reprezentace kritický oddíl, namísto funkce Win32 `EnterCriticalSection` nebo `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
