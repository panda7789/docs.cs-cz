---
title: "IHostCrst – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst
helpviewer_keywords: IHostCrst interface [.NET Framework hosting]
ms.assetid: ac298ebd-0815-47e4-a823-30b31baab903
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 59485d7a642ba8b3233d5d077062e89fb2ac9b14
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrst-interface"></a>IHostCrst – rozhraní
Slouží jako reprezentace hostitele kritické oddílu pro dělení na vlákna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ENTER – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-enter-method.md)|Zadá kritická sekce.|  
|[Leave – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-leave-method.md)|Ponechá kritická sekce.|  
|[Setspincount – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-setspincount-method.md)|Nastaví počet typu číselník pro kritická sekce.|  
|[TryEnter – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-tryenter-method.md)|Pokusí se okamžitě zadejte kritická sekce a sestavy úspěšná nebo neúspěšná.|  
  
## <a name="remarks"></a>Poznámky  
 `IHostCrst`umožňuje modul CLR (CLR) a komunikovat přímo s hostitele reprezentace kritické oddílu, nikoli pomocí Win32 funkce, jako třeba `EnterCriticalSection` nebo `LeaveCriticalSection`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iclrsyncmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [Ihostsyncmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
