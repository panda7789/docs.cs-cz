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
ms.openlocfilehash: b7fc0a271a9c62406d2942f387a5458e21211116
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522723"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager – rozhraní
Poskytuje metody, které umožní modul CLR (CLR) ke konfiguraci fondu vláken a zařadit do fronty pracovních položek s fondem vláken.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAvailableThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Získá počet vláken ve fondu vláken, která nejsou aktuálně zpracování pracovní položky.|  
|[GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Získá maximální počet vláken, která udržuje hostiteli současně ve fondu vláken.|  
|[GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Získá minimální počet nečinných vláken, které udržuje hostitele čekat na případná požadavků.|  
|[QueueUserWorkItem – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Zařadí do fronty pro spuštění funkce a obsahuje objekt, který obsahuje data pro funkce.|  
|[SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Nastaví maximální počet vláken, které hostitele může udržovat ve fondu vláken.|  
|[SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Nastaví minimální počet nečinných vláken, které hostitele, musíte mít v předvídání požadavků.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel není vyžadován konfigurace s použitím hodnoty zadané ve volání do fondu vláken `SetMaxThreads` a `SetMinThreads` metody. V takovém případě hostitele by měl vrátit hodnotu HRESULT E_NOTIMPL z těchto metod.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
