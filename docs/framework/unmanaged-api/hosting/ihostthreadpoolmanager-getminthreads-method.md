---
title: IHostThreadPoolManager::GetMinThreads – metoda
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager.GetMinThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager::GetMinThreads
helpviewer_keywords:
- IHostThreadPoolManager::GetMinThreads method [.NET Framework hosting]
- GetMinThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: dc07232b-b2e4-4dab-87e2-3c955974ab48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1230a72d06677b4d36d10a8a31d63638c1fcd41
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170687"
---
# <a name="ihostthreadpoolmanagergetminthreads-method"></a>IHostThreadPoolManager::GetMinThreads – metoda
Získá minimální počet nečinných vláken, které udržuje hostitele ve fondu vláken čekat na případná požadavků.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMinThreads (  
    [out] DWORD *MinThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `MinThreads`  
 [out] Ukazatel na minimální počet nečinných pracovních vláken, které aktuálně uchovává hostitele.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`GetMinThreads` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Hostitel neposkytuje implementaci `GetMinThreads`.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel není potřeba zajišťovat implementaci rozhraní `GetMinThreads`. V tomto případě měla by vrátit hodnotu HRESULT E_NOTIMPL.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadPool.GetMinThreads%2A>
- <xref:System.Threading.ThreadPool>
- [GetMaxThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)
- [SetMinThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)
- [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
