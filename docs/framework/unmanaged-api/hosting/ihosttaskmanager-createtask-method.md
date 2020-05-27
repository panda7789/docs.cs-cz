---
title: IHostTaskManager::CreateTask – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CreateTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CreateTask
helpviewer_keywords:
- CreateTask method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::CreateTask method [.NET Framework hosting]
ms.assetid: a6f8ad36-61e1-42b0-9db2-add575646d18
topic_type:
- apiref
ms.openlocfilehash: 7079a915c0402df62afa5648317619af82c943b0
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841977"
---
# <a name="ihosttaskmanagercreatetask-method"></a>IHostTaskManager::CreateTask – metoda
Požaduje, aby hostitel vytvořil novou úlohu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateTask (  
    [in]  DWORD stacksize,
    [in]  LPTHREAD_START_ROUTINE pStartAddress,  
    [in]  PVOID pParameter,  
    [out] IHostTask **ppTask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `stacksize`  
 pro Požadovaná velikost vyžádaného zásobníku (v bajtech), nebo 0 (nula) pro výchozí velikost.  
  
 `pStartAddress`  
 pro Ukazatel na funkci, kterou má úkol provést.  
  
 `pParameter`  
 pro Ukazatel na uživatelská data, která mají být předána funkci, nebo hodnotu null, pokud funkce nepřijímá žádné parametry.  
  
 `ppTask`  
 mimo Ukazatel na adresu instance [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) vytvořeného hostitelem nebo hodnotu null, pokud úlohu nelze vytvořit. Úloha zůstane v pozastaveném stavu, dokud není explicitně spuštěna voláním metody [IHostTask:: Start](ihosttask-start-method.md).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateTask`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pro vytvoření požadované úlohy není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR volá `CreateTask` požadavek na to, aby hostitel vytvořil nový úkol. Hostitel vrátí ukazatel rozhraní na `IHostTask` instanci. Vrácený úkol musí zůstat pozastaven, dokud není explicitně spuštěn voláním metody `IHostTask::Start` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
