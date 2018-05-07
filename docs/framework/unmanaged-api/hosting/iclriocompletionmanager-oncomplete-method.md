---
title: ICLRIoCompletionManager::OnComplete – metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c11fa66ed583df93accc8ff1e5e95164d4de659d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete – metoda
Modul CLR (CLR) upozorní stavu požadavek vstupně-výstupních operací, která byla vytvořená pomocí volání [ihostiocompletionmanager::Bind –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 [v] Hodnota HRESULT, které uvádí stav operace vazby.  
  
-   S_OK označuje, že operace úspěšně dokončena.  
  
-   HOST_E_INTERRUPTED označuje, že volání ukončeno před dokončením.  
  
-   E_FAIL označuje, že došlo k neznámé, neopravitelné, závažnou chybu.  
  
 `NumberOfBytesTransferred`  
 [v] Počet bajtů přenesených během zpracování požadavku vstupně-výstupní operace.  
  
 `pvOverlapped`  
 [v] Ukazatel `OVERLAPPED` struktura, která byla předána volání `IHostIoCompletionManager::Bind` metoda.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`OnComplete` úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.|  
|E_FAIL|Došlo k neznámému závažné selhání. Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu. Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud se hostitel implementuje abstrakci dokončení vstupně-výstupních operací, modulu CLR provede vstupně-výstupní požadavky přes hostitele pomocí metody [ihostiocompletionmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md). Hostitel pak zavolá `OnComplete` metoda upozornit běhové prostředí na výsledek takových žádostí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
