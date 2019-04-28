---
title: IHostSyncManager::CreateAutoEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateAutoEvent
helpviewer_keywords:
- IHostSyncManager::CreateAutoEvent method [.NET Framework hosting]
- CreateAutoEvent method [.NET Framework hosting]
ms.assetid: 3153643e-cf5c-4b44-8e0e-c2b22cb08208
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9c91a982a5f3d28b43a301f961601485639bb91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696649"
---
# <a name="ihostsyncmanagercreateautoevent-method"></a>IHostSyncManager::CreateAutoEvent – metoda
Vytvoří objekt události automatického obnovení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateAutoEvent (  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEvent`  
 [out] Ukazatel na adresu [ihostautoevent –](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md) instanci implementovaného tímto hostitelem, nebo hodnotu null, pokud nelze vytvořit objekt události.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateAutoEvent` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Nedostatek paměti nebyly k dispozici k vytvoření objektu požadovanou událost.|  
  
## <a name="remarks"></a>Poznámky  
 `CreateAutoEvent` Vytvoří objekt automatické událostí jehož stav se automaticky změní na nesignálového po vydala vlákno čekání. Tato metoda zrcadlí Win32 `CreateEvent` funkci s hodnotou `false` zadaný pro `bManualReset` parametr  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
- [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
