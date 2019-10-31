---
title: ICLRTaskManager::CreateTask – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type:
- apiref
ms.openlocfilehash: fcb78dd5374ff97f23d7dfea63fe33fa96836958
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124534"
---
# <a name="iclrtaskmanagercreatetask-method"></a>ICLRTaskManager::CreateTask – metoda
Požadavky explicitně, aby modul CLR (Common Language Runtime) vytvořil nový úkol.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pTask`  
 mimo Ukazatel na adresu nově vytvořeného [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)nebo hodnotu null, pokud úlohu nebylo možné vytvořit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|K přidělení požadovaného prostředku není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR vytvoří automaticky nový úkol po inicializaci, když uživatelský kód vytvoří vlákno pomocí typů v oboru názvů <xref:System.Threading> nebo při zvýšení velikosti fondu vláken. Také vytvoří úlohy, pokud nespravovaný kód provede volání spravované funkce.  
  
 `CreateTask` umožňuje hostiteli vytvořit explicitní požadavek, který vytvoří nový úkol CLR. Například hostitel může vyvolat tuto metodu pro předinicializaci datových struktur.  
  
> [!IMPORTANT]
> Nový úkol se vrátí v pozastaveném stavu a zůstane pozastaven, dokud hostitel explicitně nevolá [IHostTask:: Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
