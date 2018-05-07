---
title: IHostThreadPoolManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92097cdf735630f3537296f188bd83ea8162add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager – rozhraní
Poskytuje metody, které umožní modul CLR (CLR) ke konfiguraci fondu vláken a do fronty pracovních položek pro fond vláken.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAvailableThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.|  
|[GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Získá maximální počet vláken, která udržuje hostitele současně ve fondu vláken.|  
|[GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Získá minimální počet nečinných vláken, která udržuje hostitele v předvídání požadavků.|  
|[QueueUserWorkItem – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Funkce pro spuštění front a poskytuje objekt obsahující data, která má být používána funkce.|  
|[SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, které hostitele může udržují ve fondu vláken.|  
|[SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Nastaví minimální počet nečinných vláken, která musí zachovat hostitele v předvídání požadavků.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel není potřeba konfigurovat fond vláken pomocí hodnoty zadané ve volání `SetMaxThreads` a `SetMinThreads` metody. V takovém případě by měl vrátit hostitele má hodnotu HRESULT E_NOTIMPL z těchto metod.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
