---
title: "IHostThreadPoolManager::GetMaxThreads – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.GetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::GetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMaxThreads method [.NET Framework hosting]
- GetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: db268876-6178-4a81-aca3-318ee7f96001
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84867f1b5dfdcfd7a50d01c9e51cb0c42da62f0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagergetmaxthreads-method"></a>IHostThreadPoolManager::GetMaxThreads – metoda
Získá maximální počet vláken, která udržuje hostitele současně ve fondu vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMaxThreads (  
    [out] DWORD *pdwMaxWorkerThreads  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwMaxWorkerThreads`  
 [out] Ukazatel na maximální počet vláken, která udržuje hostitele ve fondu vláken.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetMaxThreads`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul common language runtime (CLR (nebyla načtena do procesu, nebo CLR je ve stavu, ve kterém it nelze spravovaného kódu nebo proces volání úspěšně spustit.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Hostitel neposkytuje implementace `GetMaxThreads`.|  
  
## <a name="remarks"></a>Poznámky  
 Volání CLR `GetMaxThreads` můžete určit celkový počet vláken ve fondu vláken. [Getavailablethreads –](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md) metoda získá počet vláken, která nejsou aktuálně zpracování pracovní položky. Všechny požadavky výše vrácená hodnota `pdwMaxWorkerThreads` parametr zůstanou ve frontě, dokud vláken k dispozici.  
  
 Pokud hostitel neposkytne implementace `GetMaxThreads`, má hodnotu HRESULT E_NOTIMPL má být vrácen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ThreadPool.GetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [GetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)  
 [SetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)  
 [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
