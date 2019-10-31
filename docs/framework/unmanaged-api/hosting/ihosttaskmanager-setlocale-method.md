---
title: IHostTaskManager::SetLocale – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: e560d08d3e10db1b5978d1bd7be53dfed9ca3268
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132974"
---
# <a name="ihosttaskmanagersetlocale-method"></a>IHostTaskManager::SetLocale – metoda
Upozorňuje hostitele, že modul CLR (Common Language Runtime) změnil národní prostředí nebo jazykovou verzi v aktuálně vykonávané úloze.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lcid`  
 pro Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazenou geografickou jazykovou verzi a jazyk.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetLocale` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Hostitel nepovoluje spravovanému kódu uživatele upravovat národní prostředí.|  
  
## <a name="remarks"></a>Poznámky  
 Běhové volání `SetLocale` při změně hodnoty vlastnosti <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> spravovaným kódem. Tato metoda poskytuje možnost pro hostitele, aby vykonává jakékoli mechanismy, které může být pro synchronizaci národních prostředí. Pokud hostitel nepovoluje změnu národního prostředí ze spravovaného kódu nebo neimplementuje mechanismus pro synchronizaci lokálních hodnot, měla by vrátit E_NOTIMPL z této metody.  
  
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
- [SetUILocale – metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
