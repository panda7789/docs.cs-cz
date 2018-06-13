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
ms.openlocfilehash: 88f2ef8299911905d651ad5c3076dc9c74f397f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438916"
---
# <a name="ihostcrst-interface"></a>IHostCrst – rozhraní
Slouží jako reprezentace hostitele kritické oddílu pro dělení na vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Enter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Zadá kritická sekce.|  
|[Leave – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Ponechá kritická sekce.|  
|[SetSpinCount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Nastaví počet typu číselník pro kritická sekce.|  
|[TryEnter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Pokusí se okamžitě zadejte kritická sekce a sestavy úspěšná nebo neúspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostCrst` umožňuje modul CLR (CLR) a komunikovat přímo s hostitele reprezentace kritické oddílu, nikoli pomocí Win32 funkce, jako třeba `EnterCriticalSection` nebo `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
